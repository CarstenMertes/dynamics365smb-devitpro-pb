---
title: Feature Telemetry
description: Learn about the telemetry that you can emit from features in Business Central.  
author: bholtorf
ms.topic: conceptual
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: administration, tenant, admin, environment, sandbox, telemetry, data, sensitive
ms.date: 05/01/2021
ms.author: bholtorf
---

# Feature Telemetry

The Telemetry AL module simplifies the way you monitor the health of your solution and the uptake of application features. There are multiple benefits of using the module compared to sending telemetry via `Session.LogMessage`. For example:

* Different features can be compared across the same metrics.
* Common information is sent together with every feature telemetry message, which allows for advanced filtering capabilities.

## Example: Register the use of a feature

It's easy to use the Feature Telemetry codeunit. For example, to register the usage of a feature, you can just use the `FeatureTelemetry.LogUsage(<tag>, <feature name>, <event name>);` method. After the telemetry is emitted, you can aggregate and display the data. For example, you can use the **Feature Usage** Power BI report. The report is available on our [BCTech](https://github.com/microsoft/BCTech/blob/master/samples/AppInsights/AL/FeatureTelemetry/Feature%20Usage.pbix) GitHub repository.

:::image type="content" source="../media/FeatureUsageReport.png" alt-text="The FeatureUsage Power BI report":::

There are three kinds of events that a feature can log through the Feature Telemetry codeunit.

`FeatureTelemetry.<LogUsage|LogError|LogUptake>(...)`

* `LogUsage` should be called when the feature is successfully used by a user. 
* `LogError` should be called when an error must be explicitly sent to telemetry. For example, after a call to a try function, when `Codeunit.Run` returned false, when sending an http response error message, and so on.
* `LogUptake` should be called when a user changes the uptake state of a feature. There are four uptake states for features:
  * `Undiscovered`  
  * `Discovered`  
  * `Set up`  
  * `Used`  

> [!NOTE]
> Tracking the uptake status of a feature may make database transactions. If `LogUptake` is called from within a try function, the `PerformWriteTransactionsInASeparateSession` parameter should be set to `True`.

Calling `LogUptake` when the uptake state is `Undiscovered` resets the uptake state of the feature. The telemetry from this call will be used to calculate the values in the uptake funnel of the feature.

## Log uptake

If a feature logs uptake, there should be calls to register the `Discovered`, `Set up`, and `Used` states. The following list describes the current convention for registering uptake states:

* `Discovered` should be registered when pages related to the given feature are opened (or when a user looks for information about a feature).
* `Set up` should be registered when the user performed a set up for the feature (usually right after a record in a table related to the feature is added or updated).
* `Used` should be registered when a user attempts to use the feature (note the difference with LogUsage, which should be called only if the feature is used successfully).

If `LogUptake` is called from a try function, the `PerformWriteTransactionsInASeparateSession` parameter should be set to `true`.

## Feature and event names

Feature names should be short and easy to identify. For example, Retention policies, Configuration packages, and Emailing. Event names should specify the scenario being executed. If `LogUsage` is called, the event name should use the past tense because the event has already happened. For example, `Email sent` or `Retention policy applied`. If `LogError` is called, the event name should use the present tense. For example, `Sending email`, `Loading template`).

## General dimensions

|Dimension  | Description or value  |
|---------|---------|
|message     | Depends on the event.        |
|severityLevel     |**1**         |

## Custom dimensions

|Dimension  | Description or value  |
|---------|---------|
|aadTenantId|Specifies the Azure Active Directory (Azure AD) tenant ID used for Azure AD authentication. For on-premises, if you aren't using Azure AD authentication, this value is **common**.|
|alCategory     | **FeatureTelemetry**.  |
|alFeatureName  | The name of the feature being tracked.  |
|alSubCategory     | Holds one of the values **Uptake**, **Usage**, or **Error**.  |
|alFeatureUptakeStatus| If alSubCategory holds the value **Uptake**, then the update status can hold one the the following values: **Discovered**, **Set up**, **Undiscovered**, or **Used**.
|alCallerAppName     | The name of the extension that emitted telemetry.      |
|alCallerAppVersionMajor     | The major version of the extension that emitted telemetry. |
|alCallerAppVersionMinor     | The minor version of the extension that emitted telemetry.        |
|alClientType     | The client type of the session.        |
|alCompany     | The current company name.       |
|alIsEvaluationCompany | [!INCLUDE[environmentType](../includes/include-telemetry-dimension-is-evaluation-company.md)] |
|alTenantLicenseState     | [!INCLUDE[environmentType](../includes/include-telemetry-dimension-tenant-license-state.md)] |
|alIsAdmin     | [!INCLUDE[environmentType](../includes/include-telemetry-dimension-is-tenant-admin.md)]|
|alCountryCode     | [!INCLUDE[environmentType](../includes/include-telemetry-dimension-country-code.md)] |
|alDataClassification|**SystemMetadata**. Fixed and set by the Feature Telemetry codeunit.|
|alObjectId     | **8713**. The object ID of the Feature Telemetry codeunit.        |
|alObjectName     | **System Telemetry Logger**. The name of the codeunit used by the Feature Telemetry codeunit. |
|alUserRole| The profile ID associated with the user in the User Personalization table.|
|component|**Dynamics 365 Business Central Server**|
|componentVersion|Specifies the version number of the component that emits telemetry (see the **component** dimension).|
|environmentName|Specifies the name of the tenant environment. See [Managing Environments](/dynamics365/business-central/dev-itpro/administration/tenant-admin-center-environments). This dimension isn't included for [!INCLUDE[prod_short](../developer/includes/prod_short.md)] on-premises environments.|
|environmentType|Specifies the environment type for the tenant, such as **Production**, **Sandbox**, **Trial**. See [Environment Types](/dynamics365/business-central/dev-itpro/administration/tenant-admin-center-environments).|
|telemetrySchemaVersion|Specifies the version of the Business Central telemetry schema.|
|eventId     | Unique event ID for different feature telemetry events.        |

## See Also

[Monitoring and Analyzing Telemetry](telemetry-overview.md)  
[Enable Sending Telemetry to Application Insights](telemetry-enable-application-insights.md)  
[Feature Telemetry sample](https://github.com/microsoft/BCTech/tree/master/samples/AppInsights/AL/FeatureTelemetry)  
