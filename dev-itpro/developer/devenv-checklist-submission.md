---
title: Technical validation checklist
description: Describes the steps you must go through to successfully submit your app to AppSource using AppSourceCop for Business Central.
author: SusanneWindfeldPedersen
ms.custom: na
ms.date: 02/28/2023
ms.reviewer: solsen
ms.topic: conceptual
ms.author: freddyk
---

# Technical validation

Below you find a checklist of all requirements that you **must meet before submitting** an extension for validation. You also find a description of how the [!INCLUDE [prod_short](includes/prod_short.md)] Validation team is performing technical and manual validation and how you can implement a validation pipeline to perform the same technical validation yourself.

> [!TIP]  
> If you have questions around validation for your app, see [Technical Validation FAQ](devenv-checklist-submission-faq.md) for more information about who to contact.

## Technical Validation Checklist

If you don't meet these mandatory requirements, your extension fails validation. To get code validation helping you bring your extension package to AppSource, you can enable the **AppSourceCop** code analyzer. For more information, see [Using the Code Analysis Tool](devenv-using-code-analysis-tool.md).

|Requirement|Example/Guidance|
|-----------|----------------|
|Develop your extension in Visual Studio Code.|[Developing [!INCLUDE[d365al_ext_md](../includes/d365al_ext_md.md)]s](devenv-dev-overview.md)|
|The app.json file has mandatory properties that you must include. The 'name', 'publisher', and 'version' properties must match the values set in your offer description. Here you can also read more about dependency syntax and multiple countries/regions per a single app syntax.|[Mandatory app.json properties](devenv-json-files.md)|
|Coding of `Date` must follow a specific format (**no longer region-specific**)|Use the format `yyyymmddD`. For example, `20170825D`.|
|Remote services (including all Web services calls) can use either HTTP or HTTPS. However, HTTP calls are only possible by using the HttpRequest AL type.|[Guidance on HTTP use](devenv-restapi-overview.md)|
|Only JavaScript based Web client add-ins are supported. The zipping process is handled automatically by the compiler. Include the new AL `controladdin` type, JavaScript sources, and build the app.|[Control Add-Ins](devenv-control-addin-object.md)|
|The .app file must be digitally signed.|[Sign an APP Package File](devenv-sign-extension.md)|
|Set the application areas that apply to your controls. Failure to do so will result in the control not appearing in [!INCLUDE[d365fin_long_md](includes/d365fin_long_md.md)].|[Application Area guidance](properties/devenv-applicationarea-property.md)|
|Permission set(s) must be created by your extension and when marked, should give the user all setup and usage abilities. A user must not be required to have SUPER permissions for setup and usage of your extension.|[Exporting Permission Sets](devenv-export-permission-sets.md)<br>[Managing Users and Permissions](/dynamics365/business-central/ui-how-users-permissions)|
|Before submitting for validation, ensure that you can publish/sync/install/uninstall/reinstall your extension. **This must be done in a [!INCLUDE[d365fin_long_md](includes/d365fin_long_md.md)] environment**.|[How to publish your app](devenv-how-publish-and-install-an-extension-v2.md)|
|Thoroughly test your extension in a [!INCLUDE[d365fin_long_md](includes/d365fin_long_md.md)] environment.|[Testing Your Extension](../compliance/apptest-testingyourextension.md)|
|Don't use `OnBeforeCompanyOpen` or `OnAfterCompanyOpen`|[Replacement Options](../compliance/apptest-onbeforecompanyopen.md)|
|Include the proper upgrade code allowing your app to successfully upgrade from version to version.|[Upgrading Extensions](devenv-upgrading-extensions.md)|
|Pages and code units that are designed to be exposed as Web services must not generate any UI that would cause an exception in the calling code.|[Web Services Usage](../compliance/apptest-webservices.md)|
|You're required to register affixes for your publisher name and to use them in your extension.|[Prefix/Suffix Guidelines](../compliance/apptest-prefix-suffix.md)|
|You're required to register an ID range for your publisher name and to use it in your extension.|[Object Ranges](readiness/get-started.md#requesting-an-object-range)|
|We strongly recommend you're using automated testing, using the AL Test Toolkit. You aren't required to include the test package with your extension.|[Test the advanced sample extension](devenv-extension-advanced-example-test.md)|
|DataClassification is required for fields of all tables/table extensions. Property must be set to other than `ToBeClassified`.|[Classifying Data](devenv-classifying-data.md)|
|You must use the Profile object to add profiles instead of inserting them into the **Profiles** table.|[Profile Object](devenv-profile-object.md)|
|Use `addfirst` and `addlast` for placing your actions on Business Central pages. This eliminates breaking your app due to Business Central core changes.|[Placing Actions and Controls](devenv-page-ext-object.md#using-keywords-to-place-actions-and-controls)|
|The extension submitted must not be a runtime package.|[Creating Runtime Packages](devenv-creating-runtime-packages.md)|
|The extension submitted must use translation files.|[Working with Translation Files](devenv-work-with-translation-files.md)|
|The extension submitted must specify the `Application` manifest property.|The `Application` manifest property is required in order to compute the minimum release of Business Central targeted by your submission. For more information, see [Computation of Releases for Validation](#against-which-releases-of-business-central-is-your-submission-validated)|
|The extension submitted should have a unique `AppId`.| Every extension should have a unique `AppId` and it's not allowed to submit PTEs and AppSource apps with the same `AppId`. Also see [Constraints on extension types](devenv-extension-types-and-scope.md#constraints-on-extension-types).

## Technical validation performed by the Business Central services

The primary responsibility of the technical validation is to ensure that the [!INCLUDE [prod_short](includes/prod_short.md)] online service is stable and that the apps can be installed and run without destabilizing the service.

The technical validation is fully automated and validates the requirements defined in the technical validation checklist above.

> [!Important]  
> It's recommended that all partners run the self-validation documented in the following steps, before submitting apps for validation to maximize chances of validation success.

1. The manifest of all extensions in the submission is validated. If any **mandatory properties or required property values are missing, the submission is rejected.**.
2. The registration of affixes for the publisher name of all the extensions in the submission is validated. If **the publisher name does not have any registered affixes, the submission is rejected.**
3. The signature of all extensions in the submission are validated. If any **extension is not signed or its signature is not valid, the submission is rejected.**
4. The consistency of the main extension information (name, publisher, version) is validated against the offer description. If any **differences are noticed, the submission is rejected.**
5. The extensions in the submission are validated. If **any runtime packages are present, the submission is rejected.**

Once the extension has passed these first validation steps, the minimum release for your submission is computed as described in [Computation of Releases for Validation](devenv-checklist-submission.md#against-which-releases-of-business-central-is-your-submission-validated).

For **each country and each release** targeted by your submission, the following steps are run **for each extension** in the submission:

1. If the extension with the same version has already been validated for the country, further validation for this extension is skipped.
2. The set of dependencies for your extension is resolved. **Any unresolved dependencies will cause the submission to be rejected. If you include extensions created by Microsoft in your submission, it will also be rejected.**

> [!Note]  
> You're required to include the dependencies for your extension as part of your submission only if you're submitting a newer version for them. If you don't include them in your submission, they will be downloaded automatically if they are available in [!INCLUDE [prod_short](includes/prod_short.md)] for the targeted countries/regions. If you're making your libraries available in new countries/regions, you should increase the version number.

3. The set of baselines for your extension is resolved by using the [App Management API](../administration/appmanagement/app-management-api.md).
4. The extension is compiled against the set of dependencies resolved. If the **compilation fails, the submission is rejected.**
5. The extension is tested against the resolved baselines using the AppSourceCop analyzer. If any **violations or breaking changes are identified, the submission is rejected.**
6. If the **runtime version of the extension is not supported by the release targeted, the submission is rejected.**

Additionally, if the extension submitted isn't the latest version and a higher version is available in the AppSource marketplace, additional validation is performed:

1. The next version of your extension and its dependencies are resolved using the [App Management API](../administration/appmanagement/app-management-api.md).
2. The next version of your extension is tested against the version you submitted using the AppSourceCop analyzer. If any **violations or breaking changes are identified, the submission is rejected.**  

If all extensions in the submission succeed the validation for each country and release without errors, **the submission is accepted.**.

## Running technical validation yourself

With the latest version of BcContainerHelper, you can run a single command, which should perform the same validation steps and give you a good indication of whether your apps pass validation or not:

```powershell
$validationResults = Run-AlValidation `
    -validateCurrent `
    -installApps @( "path/url to your foreign dependencies, apps which will not be part of the validation (or blank if this is the first)" ) `
    -previousApps @( "path/url to your previous version of the .app files (or blank if this is the first)" ) `
    -apps @( "path/url to the new version of the .app files" ) `
    -countries @( "countries you want to validate against (f.ex. us,ca)" ) `
    -affixes @( "affixes you own (f.ex. fab,con)" ) `
    -supportedCountries @( "supported countries (f.eks. us,ca)" )
$validationResults | Write-Host -ForegroundColor Red
```

All array parameters can also be specified as a comma-separated string. For more information, you can also check this blog post [Run-AlValidation and Run-AlCops](https://freddysblog.com/2020/12/03/run-alvalidation-and-run-alcops/).

Include app and all library apps in both previousApps and apps and also include all countries/regions on which you want to validate.

> [!NOTE]  
> The Run-AlValidation can't see whether the affixes to specify have been correctly registered with Microsoft using your MPN ID and app publisher name, please make sure registration is in place.

> [!Important]  
> The computer on which you run this command must have Docker and the latest `BcContainerHelper` PowerShell module installed and be able to run [!INCLUDE [prod_short](includes/prod_short.md)] on Docker.
>
> If you're having issues with [!INCLUDE [prod_short](includes/prod_short.md)] on Docker, you might be able to find help here: [https://freddysblog.com/2020/10/12/troubleshooting-business-central-on-docker](https://freddysblog.com/2020/10/12/troubleshooting-business-central-on-docker).
>
> You can use [https://aka.ms/getbc?artifacturl=bcartifacts%2fsandbox%2f%2fus%2flatest](https://aka.ms/getbc?artifacturl=bcartifacts%2fsandbox%2f%2fus%2flatest) to create an Azure VM, which has all prerequisites installed to run [!INCLUDE [prod_short](includes/prod_short.md)] on Docker.

> [!NOTE]  
> It is recommended that all partners set up DevOps processes to ensure that this validation process happens automatically and regularly.
>
> You can find resources for how to set up full plug-and-play DevOps processes using AL-Go for Github: [https://aka.ms/AL-Go](https://aka.ms/AL-Go).

## How to get more information on the technical validation failures?

Detailed validation results are automatically logged to telemetry in the the [!INCLUDE[appinsights](../includes/azure-appinsights-name.md)] resource specified in the manifest of the main extension in your submission.

In order to enable partner telemetry in your extension, you must specify the `applicationInsightsConnectionString` property in the manifest (app.json) of your extension. For more information about this property, see [JSON files](devenv-json-files.md).

In order to get started on analyzing your validation results, you can use this troubleshooting guide [Dynamics 365 Business Central Troubleshooting Guide (TSG) - AppSource Submission Results (SaaS)](https://github.com/microsoft/BCTech/tree/master/samples/AppInsights/TroubleShootingGuides/D365BC%20Troubleshooting%20Guides%20(TSG)/content/AppSource-Submission-TSG.ipynb).

For more information about the signals sent to telemetry during the technical validation, see [Analyzing AppSource Submission Validation Telemetry](../administration/telemetry-appsource-submission-validation-trace.md).

> [!NOTE]  
> You can setup alerts on validation telemetry. For example, you can send a daily/weekly notification to Teams/email on all validation failures across all your apps. For more information, see [Alerting on Telemetry](../administration/telemetry-alert.md).


## Against which releases of Business Central is your submission validated?

Extensions submitted to the AppSource marketplace are validated for all countries/regions specified in the submission against all the release targeted by the submission. As part of the validation, the minimum release for your submission is computed. The extensions are then validated for all releases from this minimum release to the current release in production. For example, if the minimum release for your submission is 18.0 and the latest minor release in production is 18.3, your submission is validated against 18.0, 18.1, 18.2, and 18.3.

The minimum release for your submission is computed based on the `application` property specified in the app.json of your extension. 

> [!NOTE]  
> If multiple extensions are contained in your submission, the minimum release for the submission is the highest minimal release computed for each of the extensions in the submission.

> [!NOTE]  
> The telemetry sent during the technical validation contains details about validation success/failure against each release of Business Central specified above. For more information, see [Analyzing AppSource Submission Validation Telemetry](../administration/telemetry-appsource-submission-validation-trace.md).


> [!Important]  
> The minimum release computed for your submission also defines the availability in Business Central of all the extensions in your submission.
>
> For example, if the minimum release computed is 18.1, your extensions will be available starting from release 18.1.

#### Example

If your extension's manifest is defined as follows, the minimum release where your extension can be installed is 18.0 because the manifest requires the Application extension to be available with a version higher or equal to 18.0.0.0.

```JSON
{
  "application": "18.0.0.0",
}
```

The minimum release of the extension is then 18.0.

For AppSource extensions, it's now required to use the `application` property instead of explicit dependencies on the `Base Application` and `System Application`. For more information, see [The Microsoft_Application.app File](devenv-application-app-file.md) and [AS0085](/dynamics365/business-central/dev-itpro/developer/analyzers/appsourcecop).

<!-- ### How to specify a maximum release for your extension?

In order to specify the maximum release for your extension, you must include a file named `submissionManifest.json` along with your libraries in Partner Center. This submission manifest allows you to specify the release for which your extension should stop being validated.

For instance, the following submission manifest indicates that the extension will be validated for all releases versions from the minimum release version until 18.0 excluded. If the minimum release for the submission is 17.3, this means that this extension will be validated for 17.3, 17.4, and 17.5.

```JSON
{
  "incompatibleFromRelease": "18.0"
}
``` 

> [!Important]  
> The maximum release specified for your submission also defines the availability of all the extensions in your submission as they will be marked as incompatible from this release.
>
> For example, if the maximum release specified is 18.0, your extensions will not be available for environments running on 18.0 or higher.
>
> If you do not provide a version of your extension that is compatible with this release of Business Central, your extension will cause a failure to upgrade the environments where your extension is installed. For more information about maintaining extensions, see [Maintain AppSource Apps and Per-Tenant Extensions in Business Central Online](app-maintain.md).

### When should you specify a maximum release for your extension?

The `incompatibleFromRelease` property is meant to help you release a HotFix of your extension in production.

Let's imagine that your AppSource extension is available for tenants on releases from 17.0 to 17.5 with version 1.0.0.0 and is available for release 18.0 with version 2.0.0.0. You are now required to release a bug fix for customers on releases 17.0 to 17.5 that are using version 1.0.0.0. If you submit a version 3.0.0.0 of your extension, it will be validated for breaking changes version 2.0.0.0 and will be validated for all releases from 17.0 to 18.0. However it is not always possible to have one version of an extension that is compatible with all releases of Business Central.

In this case, you can create a version 1.0.0.1 of your extension and submit it with `incompatibleFromRelease` set to 18.0. This version of the extension will then only be validated for releases 17.0 to 17.5 and will be validated for breaking changes against version 1.0.0.0.

> [!IMPORTANT]
> You must not introduce new tables or tables fields as a HotFix of your extension as this will prevent environments where this extension is installed to be updated to the next release of Business Central.

-->

## See Also

[Developing [!INCLUDE[d365al_ext_md](../includes/d365al_ext_md.md)]s](devenv-dev-overview.md)
[Analyzing AppSource Submission Validation Telemetry](../administration/telemetry-appsource-submission-validation-trace.md)
