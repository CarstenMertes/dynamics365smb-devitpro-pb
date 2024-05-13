---
title: Analyzing AppSource submission validation trace telemetry
description: Learn about the telemetry for publishing apps to AppSource from Partner Center.  
author: jswymer
ms.topic: conceptual
ms.devlang: al
ms.search.keywords: administration, tenant, admin, environment, sandbox, telemetry, AppSource, validation
ms.date: 08/01/2021
ms.author: jswymer
---

# Analyzing AppSource submission validation telemetry

**APPLIES TO:** [!INCLUDE[prod_short](../includes/prod_short.md)] 2021 release wave 1, version 18.4, and later

When you submit an app to AppSource using Partner Center, it starts an automated validation process. This technical validation process ensures the extensions in the app meet the technical requirements for going live. It goes through many of the same checks described in [technical validation](/dynamics365/business-central/dev-itpro/developer/devenv-checklist-submission).

If an app's set up for it, telemetry traces are emitted to and recorded in Application Insights. The data provides details about the success or failure of different phases of the validation. For more information about setting up telemetry for an app, see [Sending Extension Telemetry to Azure Application Insights](../developer/devenv-application-insights-for-extensions.md).

> [!NOTE]  
> In order to start analyzing your validation results, use this troubleshooting guide [Dynamics 365 Business Central Troubleshooting Guide (TSG) - AppSource Submission Results (SaaS)](https://github.com/microsoft/BCTech/tree/master/samples/AppInsights/TroubleShootingGuides/D365BC%20Troubleshooting%20Guides%20(TSG)/content/AppSource-Submission-TSG.ipynb).

## Validation process overview

The validation process starts when you publish the app. The validation runs against each extension in the app, for each country/region (market) specified for the offer in Partner Center, and for each Business Central version that the submissions targets. For more information versions, see [Against which releases of Business Central is your submission validated?](../developer/devenv-checklist-submission.md#against-which-releases-of-business-central-is-your-submission-validated).

Extensions are validated using the AL compiler and the [AppSourceCop code analyzer](../developer/devenv-using-code-analysis-tool.md). Traces are emitted at different phases during the process. Each submission is assigned a unique identifier (ID). This ID is included in each trace for a submission, allowing you to query all trace related to the submission. The general flow for the validation process is illustrated below:

1. AppSource submission validation request started
2. Validation diagnostic reported for information, warnings, or errors that occur on the submission
3. Version (X), country-region (X) validation started
4. Extension (X) validation started
5. Validation diagnostic reported for each error that occurs.
6. Extension (X) validation completed (successfully or with failures)
7. *Repeat 3-5 for each extension in the submission*
8. Version (X), country-region (X) validation completed (successfully or with failures)
9. *Repeat 2-7 for other country-regions for the Business Central release (X)*
10. *Repeat 2-8 for other Business Central releases targeted by the submission*
11. AppSource submission validation request completed (successfully or with failures)

To reduce the risk of failing the AppSource validation process, review the [technical validation](/dynamics365/business-central/dev-itpro/developer/devenv-checklist-submission) checklist before you submit an app.

## <a name="validationrequeststarted"></a>AppSource submission validation request started

Occurs when an app is published from Partner Center. For more information about publishing from Partner Center, see [Review and publish a Dynamics 365 offer - Validation and publishing steps](/azure/marketplace/dynamics-365-review-publish#validation-and-publishing-steps).

### General dimensions

|Dimension|Description or value|
|---------|-----|
|message|**AppSource submission validation request started: {validationRequestId}**|

### Custom dimensions

|Dimension|Description or value|
|---------|-----|
|eventId|**LC0028**|
|countryRegions|Lists the localized versions (markets) of the app that will be validated, like **US** or **DK**. |
|extensions|Specifies information about the extensions that are part of the submission, which will be validated.|
|severity|**Information**|
|versions|Lists the [Business Central release versions](../developer/devenv-checklist-submission.md#against-which-releases-of-business-central-is-your-submission-validated) that the app will be validated against, like **19.0** or **18.4** |
|containsHotfix|Specifies whether the submission contains a hotfix of an AppSource extension.|

<!--
{"telemetrySchemaVersion":"0.1","eventId":"LC0028","validationRequestId":"0f5978be-00ff-48a6-970c-339a036e7877","extensions":"{\r\n \"Extensions\": [\r\n {\r\n \"Id\": \"a3fe8b08-c1ce-4194-aedf-a677bf5b7eb3\",\r\n \"Name\": \"AppSource Simple\",\r\n \"Publisher\": \"AppSource Publisher\",\r\n \"Version\": \"1.0.0.0\"\r\n }\r\n ]\r\n}","severity":"Information","countryRegions":"DK, US","versions":"19.0"}
-->

<a name="other"></a>**Common custom dimensions**

The following table explains other custom dimensions that are common to all AppSource submission validation traces. 

|Dimension|Description or value|
|---------|-----|
|validationRequestId|Specifies the unique identifier assigned to the app submission validation process. All traces for the submission validation will include this ID.|
|telemetrySchemaVersion|Specifies the version of the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] telemetry schema.|


## <a name="submissionrequestdiagnostic"></a>Diagnostic reported on AppSource submission validation request

Occurs during the submission validation request to report diagnostics related to the submission itself. For example, it could be that a submission has duplicate apps, or it doesn't target any Business Central release. This signal isn't necessarily an error, but can also be warning or information. This signal differs from other diagnostic signals like `LC0034`, which are reported during the compilation of one app for one country/region release.

### General dimensions

|Dimension|Description or value|
|---------|-----|
|message|**Diagnostic reported on AppSource submission validation request: {validationRequestId}**|
|severityLevel|**1** for information, **2** for warning, **3** for error|

### Custom dimensions

|Dimension|Description or value|
|---------|-----|
|eventId|**LC0038**|
|diagnosticCode|Specifies the diagnostic identifier, like AS0001 or AL0001.|
|diagnosticMessage|Specifies the diagnostic message.|
|diagnosticSeverity|**Info**, **Warning**, or **Error**. Matches the `severityLevel`. |
|containsHotfix|Specifies whether the submission contains a hotfix of an AppSource extension.|
|[See common custom dimensions](#other)||

### Sample KQL code 
This KQL code can help you get started analyzing request warnings using the LC0038 event:

```kql
traces
| where timestamp > ago(1d) // adjust as needed
| where customDimensions.eventId == 'LC0038'
| project timestamp 
, requestId = customDimensions.validationRequestId
, diagnosticCode = customDimensions.diagnosticCode
, diagnosticMessage = customDimensions.diagnosticMessage
, diagnosticSeverity = customDimensions.diagnosticSeverity
, containsHotfix = customDimensions.containsHotfix
, message
```

[!INCLUDE[telemetry_alert_learn_more](../includes/telemetry-alerting.md)]

## <a name="versioncountrystarted"></a>(Version, country-region) validation started

Occurs when the validation has started for a specific version and country/region.

### General dimensions

|Dimension|Description or value|
|---------|-----|
|message|**(Version, country-region) validation started: version {version}, country/region {countryRegion}**|
|severityLevel|**1**|

### Custom dimensions

|Dimension|Description or value|
|---------|-----|
|eventId|**LC0030**|
|allExtensions|Specifies information about the extensions that are part of the submission and extensions that the submission extensions depend on. Select the arrow to expand the dimension to see the details about each extension.|
|baselineExtensions|Specifies the previous versions of the extensions in the app and the extensions they're dependent on. These extensions form the baseline for validation if publishing a newer version of an app that's already published.|
|extensions|Specifies the extensions that are part of the submission and will be validated. Select the arrow to expand the dimension to see the details about each extension.|
|severity|**Information**|
|version|Specifies the [Business Central release versions](../developer/devenv-checklist-submission.md#against-which-releases-of-business-central-is-your-submission-validated) that the app will be validated against, like **19.0** or **18.4**.|
|containsHotfix|Specifies whether the submission contains a hotfix of an AppSource extension.|
|[See common custom dimensions](#other)||

<!--
{"telemetrySchemaVersion":"0.1","version":"19.0","eventId":"LC0030","validationRequestId":"eae270f4-5686-460c-99ec-73f9ece08fe5","baselineExtensions":"{\r\n \"Extensions\": []\r\n}","allExtensions":"{\r\n \"Extensions\": [\r\n {\r\n \"Id\": \"a3fe8b08-c1ce-4194-aedf-a677bf5b7eb3\",\r\n \"Name\": \"AppSource Simple\",\r\n \"Publisher\": \"AppSource Publisher\",\r\n \"Version\": \"1.0.0.0\"\r\n },\r\n {\r\n \"Id\": \"c1335042-3002-4257-bf8a-75c898ccb1b8\",\r\n \"Name\": \"Application\",\r\n \"Publisher\": \"Microsoft\",\r\n \"Version\": \"19.0.26075.0\"\r\n },\r\n {\r\n \"Id\": \"8874ed3a-0643-4247-9ced-7a7002f7135d\",\r\n \"Name\": \"System\",\r\n \"Publisher\": \"Microsoft\",\r\n \"Version\": \"18.0.26014.0\"\r\n },\r\n {\r\n \"Id\": \"63ca2fa4-4f03-4f2b-a480-172fef340d3f\",\r\n \"Name\": \"System Application\",\r\n \"Publisher\": \"Microsoft\",\r\n \"Version\": \"19.0.26075.0\"\r\n },\r\n {\r\n \"Id\": \"437dbf0e-84ff-417a-965d-ed2bb9650972\",\r\n \"Name\": \"Base Application\",\r\n \"Publisher\": \"Microsoft\",\r\n \"Version\": \"19.0.26075.0\"\r\n }\r\n ]\r\n}","countryRegion":"US","extensions":"{\r\n \"Extensions\": [\r\n {\r\n \"Id\": \"a3fe8b08-c1ce-4194-aedf-a677bf5b7eb3\",\r\n \"Name\": \"AppSource Simple\",\r\n \"Publisher\": \"AppSource Publisher\",\r\n \"Version\": \"1.0.0.0\"\r\n }\r\n ]\r\n}","severity":"Information"}
-->



## <a name="extensionvalidationstarted"></a>Extension validation started

Occurs when the validation for a specific extension the submission has started.

### General dimensions

|Dimension|Description or value|
|---------|-----|
|message|**Extension validation started: version {version}, country/region {countryRegion} for extension {extensionName} version {extensionVersion} by {extensionPublisher} ({extensionId})**|
|severityLevel|**1**|

### Custom dimensions

|Dimension|Description or value|
|---------|-----|
|eventId|**LC0032**|
|countryRegion|Specifies the localized version of the app that will be validated. |
|extensionId|Specifies the ID of the extension in the submission that will be validated.|
|extensionName|Specifies the name of the extension in the submission that will be validated.|
|extensionPublisher|Specifies the publisher of the extension in the submission that will be validated.|
|extensionVersion|Specifies the version of the extension in the submission that will be validated.|
|severity|**Information**|
|version|Specifies the [Business Central release](../developer/devenv-checklist-submission.md#against-which-releases-of-business-central-is-your-submission-validated) that the extension will be validated against, like **19.0** or **18.4**.|
|hotfixValidation|Specifies whether the extension validated is a hotfix.|
|[See common custom dimensions](#other)||
<!--
{"version":"18.0","telemetrySchemaVersion":"0.1","validationRequestId":"c388ec8f-9b4a-40c3-a572-51af0722574a","extensionPublisher":"AppSource Publisher","extensionVersion":"1.0.0.0","countryRegion":"DK","extensionName":"AppSource Extension","eventId":"LC0032","extensionId":"1b8f9e14-dfc1-48c7-a8cb-d2223aa3c122","severity":"Information"}
-->

## <a name="validationdiagnosticreported"></a>Validation diagnostic reported

Occurs when an error occurs during the validation of an extension. The errors are reported by the AL compiler or by the [AppSourceCop](../developer/analyzers/appsourcecop.md) analyzer.

### General dimensions

|Dimension|Description or value|
|---------|-----|
|message|**Validation diagnostic reported: version {version}, country/region {countryRegion} for extension {extensionName} version {extensionVersion} by {extensionPublisher} ({extensionId})**|
|severityLevel|**3**|

### Custom dimensions

|Dimension|Description or value|
|---------|-----|
|eventId|**LC0034**|
|countryRegion|Specifies the localized version of the app that was validated.|
|diagnosticCode|Specifies the diagnostic identifier, like AS0001 or AL0001.|
|diagnosticMessage|Specifies the diagnostic error message.|
|diagnosticSeverity|**Error**|
|diagnosticSourceLocation|Specifies the location in the source code where the diagnostic was reported. The format used is (Line, Character).|
|diagnosticSourcePath|Specifies the path to the file where the diagnostic was reported. |
|extensionId|Specifies the ID of the extension in the submission that will be validated.|
|extensionName|Specifies the name of the extension in the submission that was validated.|
|extensionPublisher|Specifies the publisher of the extension in the submission that was validated.|
|extensionVersion|Specifies the version of the extension in the submission that was validated.|
|severity|**Error**|
|version|Specifies the [Business Central release](../developer/devenv-checklist-submission.md#against-which-releases-of-business-central-is-your-submission-validated) that the extension was validated against, like **19.0** or **18.4**.|
|hotfixValidation|Specifies whether the extension validated is a hotfix.|
|[See common custom dimensions](#other)||

<!--
{"version":"19.0","telemetrySchemaVersion":"0.1","extensionPublisher":"AppSource Publisher","extensionVersion":"1.0.0.0","extensionName":"AppSource Simple","extensionId":"a3fe8b08-c1ce-4194-aedf-a677bf5b7eb3","eventId":"LC0034","validationRequestId":"e31b8fb1-f790-457f-8a07-f3ae9bc411b2","countryRegion":"DK","severity":"Error","diagnosticSeverity":"Error","diagnosticMessage":"Only use AssertError in Test Codeunits.","diagnosticCode":"AS0058"}
-->

### Sample KQL code 
This KQL code can help you get started analyzing request failures using the LC0034 event:

```kql
traces
| where timestamp > ago(1d) // adjust as needed
| where customDimensions.eventId == 'LC0034'
| project timestamp 
, countryRegion = customDimensions.countryRegion
, version = customDimensions.version
, extensionId = customDimensions.extensionId
, extensionName = customDimensions.extensionName
, extensionPublisher = customDimensions.extensionPublisher
, extensionVersion = customDimensions.extensionVersion
, diagnosticCode = customDimensions.diagnosticCode
, diagnosticMessage = customDimensions.diagnosticMessage
, diagnosticSeverity = customDimensions.diagnosticSeverity
, diagnosticSourceLocation = customDimensions.diagnosticSourceLocation
, diagnosticSourcePath = customDimensions.diagnosticSourcePath
```

[!INCLUDE[telemetry_alert_learn_more](../includes/telemetry-alerting.md)]

## <a name="extensionvalidationcompleted"></a>Extension validation completed successfully

Occurs when the validation for a specific extension the submission has completed, and no errors occurred.

### General dimensions

|Dimension|Description or value|
|---------|-----|
|message|**Extension validation completed successfully: version {version}, country/region {countryRegion} for extension {extensionName} version {extensionVersion} by {extensionPublisher} ({extensionId})**|
|severityLevel|**1**|

### Custom dimensions

|Dimension|Description or value|
|---------|-----|
|eventId|**LC0033**|
|countryRegion|Specifies the localized version of the app that was validated. |
| extensionId|Specifies the ID of the extension in the submission that will be validated.|
| extensionName|Specifies the name of the extension in the submission that was validated.|
| extensionPublisher|Specifies the publisher of the extension in the submission that was validated.|
| extensionVersion|Specifies the version of the extension in the submission that was validated.|
|severity|**Information**|
|version|Specifies the [Business Central release](../developer/devenv-checklist-submission.md#against-which-releases-of-business-central-is-your-submission-validated) that the extension was validated against, like **19.0** or **18.4**.|
|hotfixValidation|Specifies whether the extension validated is a hotfix.|
|[See common custom dimensions](#other)||
<!--
{"telemetrySchemaVersion":"0.1","version":"19.0","extensionPublisher":"AppSource Publisher","extensionVersion":"1.0.0.0","extensionName":"AppSource Simple","extensionId":"a3fe8b08-c1ce-4194-aedf-a677bf5b7eb3","eventId":"LC0033","result":"Failure","validationRequestId":"0f5978be-00ff-48a6-970c-339a036e7877","baselineExtensions":"{\r\n \"Extensions\": []\r\n}","allExtensions":"{\r\n \"Extensions\": [\r\n {\r\n \"Id\": \"a3fe8b08-c1ce-4194-aedf-a677bf5b7eb3\",\r\n \"Name\": \"AppSource Simple\",\r\n \"Publisher\": \"AppSource Publisher\",\r\n \"Version\": \"1.0.0.0\"\r\n },\r\n {\r\n \"Id\": \"c1335042-3002-4257-bf8a-75c898ccb1b8\",\r\n \"Name\": \"Application\",\r\n \"Publisher\": \"Microsoft\",\r\n \"Version\": \"19.0.26037.0\"\r\n },\r\n {\r\n \"Id\": \"8874ed3a-0643-4247-9ced-7a7002f7135d\",\r\n \"Name\": \"System\",\r\n \"Publisher\": \"Microsoft\",\r\n \"Version\": \"18.0.26014.0\"\r\n },\r\n {\r\n \"Id\": \"63ca2fa4-4f03-4f2b-a480-172fef340d3f\",\r\n \"Name\": \"System Application\",\r\n \"Publisher\": \"Microsoft\",\r\n \"Version\": \"19.0.26037.0\"\r\n },\r\n {\r\n \"Id\": \"437dbf0e-84ff-417a-965d-ed2bb9650972\",\r\n \"Name\": \"Base Application\",\r\n \"Publisher\": \"Microsoft\",\r\n \"Version\": \"19.0.26037.0\"\r\n }\r\n ]\r\n}","countryRegion":"DK","extensions":"{\r\n \"Extensions\": [\r\n {\r\n \"Id\": \"a3fe8b08-c1ce-4194-aedf-a677bf5b7eb3\",\r\n \"Name\": \"AppSource Simple\",\r\n \"Publisher\": \"AppSource Publisher\",\r\n \"Version\": \"1.0.0.0\"\r\n }\r\n ]\r\n}","severity":"Error","failureReason":"One  more extension validation tasks have failed."}


{"telemetrySchemaVersion":"0.1","extensionPublisher":"AppSource Publisher","version":"18.1","extensionVersion":"1.0.0.0","extensionName":"AppSource Library","extensionId":"a3fe8b08-c1ce-4194-aedf-a677bf5b7eb3","eventId":"LC0033","validationRequestId":"e1e07164-f630-4b72-bd78-5807311e23ad","countryRegion":"DK","severity":"Information"}

-->

## <a name="extensionvalidationcompletedwithfailures"></a>Extension validation completed with failures

Occurs when the validation for a specific extension the submission has completed, but errors occurred.

### General dimensions

|Dimension|Description or value|
|---------|-----|
|message|**Extension validation completed with failures: version {version}, country-region {countryRegion} for extension {extensionName} version {extensionVersion} by {extensionPublisher} ({extensionId})**|
|severityLevel|**3**|

### Custom dimensions

|Dimension|Description or value|
|---------|-----|
|eventId|**LC0037**|
|countryRegion|Specifies the localized version of the app that was validated. |
| extensionId|Specifies the ID of the extension in the submission that will be validated.|
| extensionName|Specifies the name of the extension in the submission that was validated.|
| extensionPublisher|Specifies the publisher of the extension in the submission that was validated.|
| extensionVersion|Specifies the version of the extension in the submission that was validated.|
|failureReason|**One or more error diagnostics were reported. For more information about the diagnostics, see traces with eventId LC0034.**|
|severity|**Error**|
|version|Specifies the [Business Central release](../developer/devenv-checklist-submission.md#against-which-releases-of-business-central-is-your-submission-validated) that the extension was validated against, like **19.0** or **18.4**.|
|hotfixValidation|Specifies whether the extension validated is a hotfix.|
|[See common custom dimensions](#other)||
<!--
{"version":"19.0","telemetrySchemaVersion":"0.1","extensionPublisher":"AppSource Publisher","extensionVersion":"1.0.0.0","extensionName":"AppSource Simple","extensionId":"a3fe8b08-c1ce-4194-aedf-a677bf5b7eb3","eventId":"LC0037","validationRequestId":"e31b8fb1-f790-457f-8a07-f3ae9bc411b2","countryRegion":"DK","severity":"Error","failureReason":"One  more extension validation tasks have failed."}
-->

### Sample KQL code 
This KQL code can help you get started analyzing request failures using the LC0037 event:

```kql
traces
| where timestamp > ago(1d) // adjust as needed
| where customDimensions.eventId == 'LC0037'
| project timestamp 
, requestId = customDimensions.validationRequestId
, countryRegion = customDimensions.countryRegion
, version = customDimensions.version
, extensionName = customDimensions.extensionName
, failureReason = customDimensions.failureReason
```

[!INCLUDE[telemetry_alert_learn_more](../includes/telemetry-alerting.md)]

## <a name="versioncountrycompleted"></a>(Version, country-region) validation completed successfully

Occurs when the validation has completed for a specific version and country/region, and no errors occurred.

### General dimensions

|Dimension|Description or value|
|---------|-----|
|message|**(Version, country-region) validation completed successfully: version {version}, country/region {countryRegion}**|
|severityLevel|**1**|

### Custom dimensions

|Dimension|Description or value|
|---------|-----|
|eventId|**LC0031**|
|allExtensions|Specifies information about the extensions that were part of the submission and extensions that the submission extensions depend on. Select the arrow to expand the dimension to see the details about each extension.|
|baselineExtensions|Specifies the previous versions of the extensions in the app and the extensions they're dependent on. These extensions form the baseline for validation if publishing a newer version of an app that's already published.|
|countryRegion|Specifies the localized version of the app that was validated. |
|extensions|Specifies the extensions that were part of the submission and were validated. Select the arrow to expand the dimension to see the details about each extension.|
|severity|**Information**|
|version|Specifies the [Business Central release](../developer/devenv-checklist-submission.md#against-which-releases-of-business-central-is-your-submission-validated) that the app was validated against, like **19.0** or **18.4**.|
|containsHotfix|Specifies whether the (Version, country-region) validation contains a hotfix of an AppSource extension.|
|[See common custom dimensions](#other)||
<!--
{"telemetrySchemaVersion":"0.1","version":"19.0","eventId":"LC0031","result":"Failure","validationRequestId":"0f5978be-00ff-48a6-970c-339a036e7877","baselineExtensions":"{\r\n \"Extensions\": []\r\n}","allExtensions":"{\r\n \"Extensions\": [\r\n {\r\n \"Id\": \"a3fe8b08-c1ce-4194-aedf-a677bf5b7eb3\",\r\n \"Name\": \"AppSource Simple\",\r\n \"Publisher\": \"AppSource Publisher\",\r\n \"Version\": \"1.0.0.0\"\r\n },\r\n {\r\n \"Id\": \"c1335042-3002-4257-bf8a-75c898ccb1b8\",\r\n \"Name\": \"Application\",\r\n \"Publisher\": \"Microsoft\",\r\n \"Version\": \"19.0.26037.0\"\r\n },\r\n {\r\n \"Id\": \"8874ed3a-0643-4247-9ced-7a7002f7135d\",\r\n \"Name\": \"System\",\r\n \"Publisher\": \"Microsoft\",\r\n \"Version\": \"18.0.26014.0\"\r\n },\r\n {\r\n \"Id\": \"63ca2fa4-4f03-4f2b-a480-172fef340d3f\",\r\n \"Name\": \"System Application\",\r\n \"Publisher\": \"Microsoft\",\r\n \"Version\": \"19.0.26037.0\"\r\n },\r\n {\r\n \"Id\": \"437dbf0e-84ff-417a-965d-ed2bb9650972\",\r\n \"Name\": \"Base Application\",\r\n \"Publisher\": \"Microsoft\",\r\n \"Version\": \"19.0.26037.0\"\r\n }\r\n ]\r\n}","countryRegion":"DK","extensions":"{\r\n \"Extensions\": [\r\n {\r\n \"Id\": \"a3fe8b08-c1ce-4194-aedf-a677bf5b7eb3\",\r\n \"Name\": \"AppSource Simple\",\r\n \"Publisher\": \"AppSource Publisher\",\r\n \"Version\": \"1.0.0.0\"\r\n }\r\n ]\r\n}","severity":"Error","failureReason":"One  more error diagnostics were reported."}
-->

## <a name="versioncountryvalidationcompletedwithfailures"></a>(Version, country-region) validation completed with failures

Occurs when the validation has completed for a specific version and country/region, and errors occurred.

### General dimensions

|Dimension|Description or value|
|---------|-----|
|message|**(Version, country-region) validation completed with failures: version {version}, country-region {countryRegion}**|
|severityLevel|**3**|

### Custom dimensions

|Dimension|Description or value|
|---------|-----|
|eventId|**LC0036**|
|allExtensions|Specifies information about the extensions that were part of the submission and extensions that the submission extensions depend on. Select the arrow to expand the dimension to see the details about each extension.|
|baselineExtensions|Specifies the previous versions of the extensions in the app and the extensions they're dependent on. These extensions form the baseline for validation if publishing a newer version of an app that's already published.|
|countryRegion|Specifies the localized version of the app that was validated. |
|extensions|Specifies the extensions that were part of the submission and were validated. Select the arrow to expand the dimension to see the details about each extension.|
|failureReason|**One or more extension validation tasks have failed.**|
|severity|**Error**|
|version|Specifies the [Business Central release](../developer/devenv-checklist-submission.md#against-which-releases-of-business-central-is-your-submission-validated) that the app was validated against, like **19.0** or **18.4**.|
|containsHotfix|Specifies whether the (Version, country-region) validation contains a hotfix of an AppSource extension.|
|[See common custom dimensions](#other)||
<!--
{"version":"19.0","telemetrySchemaVersion":"0.1","eventId":"LC0036","validationRequestId":"24995dae-01f2-4523-b3dc-b4e54cb25c7e","countryRegion":"DK","severity":"Error","baselineExtensions":"{\r\n \"Extensions\": []\r\n}","failureReason":"One  more error diagnostics were reported.","extensions":"{\r\n \"Extensions\": [\r\n {\r\n \"Id\": \"a3fe8b08-c1ce-4194-aedf-a677bf5b7eb3\",\r\n \"Name\": \"AppSource Simple\",\r\n \"Publisher\": \"AppSource Publisher\",\r\n \"Version\": \"1.0.0.0\"\r\n }\r\n ]\r\n}","allExtensions":"{\r\n \"Extensions\": [\r\n {\r\n \"Id\": \"a3fe8b08-c1ce-4194-aedf-a677bf5b7eb3\",\r\n \"Name\": \"AppSource Simple\",\r\n \"Publisher\": \"AppSource Publisher\",\r\n \"Version\": \"1.0.0.0\"\r\n },\r\n {\r\n \"Id\": \"c1335042-3002-4257-bf8a-75c898ccb1b8\",\r\n \"Name\": \"Application\",\r\n \"Publisher\": \"Microsoft\",\r\n \"Version\": \"19.0.26290.3402\"\r\n },\r\n {\r\n \"Id\": \"8874ed3a-0643-4247-9ced-7a7002f7135d\",\r\n \"Name\": \"System\",\r\n \"Publisher\": \"Microsoft\",\r\n \"Version\": \"18.0.26244.0\"\r\n },\r\n {\r\n \"Id\": \"63ca2fa4-4f03-4f2b-a480-172fef340d3f\",\r\n \"Name\": \"System Application\",\r\n \"Publisher\": \"Microsoft\",\r\n \"Version\": \"19.0.26290.3402\"\r\n },\r\n {\r\n \"Id\": \"437dbf0e-84ff-417a-965d-ed2bb9650972\",\r\n \"Name\": \"Base Application\",\r\n \"Publisher\": \"Microsoft\",\r\n \"Version\": \"19.0.26290.3402\"\r\n }\r\n ]\r\n}"}
-->

### Sample KQL code 
This KQL code can help you get started analyzing request failures using the LC0036 event:

```kql
traces
| where timestamp > ago(1d) // adjust as needed
| where customDimensions.eventId == 'LC0036'
| project timestamp 
, requestId = customDimensions.validationRequestId
, countryRegion = customDimensions.countryRegion
, version = customDimensions.version
, extensions = customDimensions.extensions
, allExtensions = customDimensions.allExtensions
, baselineExtensions = customDimensions.baselineExtensions
, failureReason = customDimensions.failureReason
```

[!INCLUDE[telemetry_alert_learn_more](../includes/telemetry-alerting.md)]

## <a name="validationrequestcompleted"></a>AppSource submission validation request completed successfully

Occurs when the submission validation process has fully completed, and no errors occurred.

### General dimensions

|Dimension|Description or value|
|---------|-----|
|message|**AppSource submission validation request completed successfully: {validationRequestId}**|
|severityLevel|**1**|

### Custom dimensions

|Dimension|Description or value|
|---------|-----|
|eventId|**LC0029**|
|countryRegions|Lists the localized versions (markets) of the app that were validated, like **US** or **DK**.|
|extensions|Specifies information about the extensions that were part of the submission and validated.|
|severity|**Information**|
|versions|Lists the [Business Central release](../developer/devenv-checklist-submission.md#against-which-releases-of-business-central-is-your-submission-validated) that the app was validated against, like **19.0** or **18.4**. |
|containsHotfix|Specifies whether the submission contains a hotfix of an AppSource extension.|
|[See common custom dimensions](#other)||
<!--
{"telemetrySchemaVersion":"0.1","eventId":"LC0029","result":"Failure","validationRequestId":"eae270f4-5686-460c-99ec-73f9ece08fe5","extensions":"{\r\n \"Extensions\": [\r\n {\r\n \"Id\": \"a3fe8b08-c1ce-4194-aedf-a677bf5b7eb3\",\r\n \"Name\": \"AppSource Simple\",\r\n \"Publisher\": \"AppSource Publisher\",\r\n \"Version\": \"1.0.0.0\"\r\n }\r\n ]\r\n}","severity":"Error","countriesRegions":"US, CA","versions":"19.0"}
-->

## <a name="submissionrequestcompletedwithfailures"></a>AppSource submission validation request completed with failures

Occurs when the submission validation process has fully completed, but errors occurred.

### General dimensions

|Dimension|Description or value|
|---------|-----|
|message|**AppSource submission validation request completed with failures: {validationRequestId}**|
|severityLevel|**3**|

### Custom dimensions

|Dimension|Description or value|
|---------|-----|
|eventId|**LC0035**|
|countryRegions|Lists the localized versions (markets) of the app that were validated, like **US** or **DK**.|
|extensions|Specifies the extensions that were part of the submission and validated.|
|failureReason|**One  more extension validation tasks have failed.**|
|severity|**Error**|
|versions|Lists the [Business Central releases](../developer/devenv-checklist-submission.md#against-which-releases-of-business-central-is-your-submission-validated) that the app was validated against, like **19.0** or **18.4**.|
|containsHotfix|Specifies whether the submission contains a hotfix of an AppSource extension.|
|[See common custom dimensions](#other)||
<!--
{"telemetrySchemaVersion":"0.1","eventId":"LC0035","validationRequestId":"e31b8fb1-f790-457f-8a07-f3ae9bc411b2","severity":"Error","failureReason":"One  more extension validation tasks have failed.","extensions":"{\r\n \"Extensions\": [\r\n {\r\n \"Id\": \"a3fe8b08-c1ce-4194-aedf-a677bf5b7eb3\",\r\n \"Name\": \"AppSource Simple\",\r\n \"Publisher\": \"AppSource Publisher\",\r\n \"Version\": \"1.0.0.0\"\r\n }\r\n ]\r\n}","countryRegions":"[\r\n \"DK\",\r\n \"US\"\r\n]","versions":"[\r\n \"19.0\"\r\n]"}
-->

### Sample KQL code 
This KQL code can help you get started analyzing request failures using the LC0035 event:

```kql
traces
| where timestamp > ago(1d) // adjust as needed
| where customDimensions.eventId == 'LC0035'
| project timestamp 
, requestId = customDimensions.validationRequestId
, countryRegions = customDimensions.countryRegions
, versions = customDimensions.versions 
, extensions = customDimensions.extensions
, failureReason = customDimensions.failureReason
```

[!INCLUDE[telemetry_alert_learn_more](../includes/telemetry-alerting.md)]

## See also

[Telemetry overview](telemetry-overview.md)   
[Sending App Telemetry to Azure Application Insights](../developer/devenv-application-insights-for-extensions.md)   
[Alert on Telemetry](telemetry-alert.md)   
[Technical Validation Checklist](../developer/devenv-checklist-submission.md)     
[Technical Validation FAQ](../developer/devenv-checklist-submission-faq.md)  