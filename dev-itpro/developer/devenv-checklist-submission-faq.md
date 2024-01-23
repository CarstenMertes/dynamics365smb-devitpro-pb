---
title: Technical validation FAQ
description: Describes the most common questions when submitting your app to AppSource for Business Central.
author: qutreson
ms.custom: na
ms.date: 08/24/2023
ms.reviewer: solsen
ms.topic: conceptual
ms.author: qutreson
---

# Technical validation FAQ

This article addresses some of the most frequently asked questions around validation of apps for AppSource submission.

## Questions about the validation process

In the following, you can read about how submissions are handled and learn how to address the most common scenarios.

### Against which releases are my apps validated?

The extensions in your submission are validated for all the releases targeted by your submission.

Based on the app.json file of your extension, the service automatically computes the minimum release targeted by your submission and the extensions are then validated for all releases from this minimum release to the current release in production. For more information, see the example in [Technical Validation Checklist](devenv-checklist-submission.md#against-which-releases-of-business-central-is-your-submission-validated). The 'Target Release' (Current, Next Minor, Next Major) available under 'Supplemental Content' in Partner Center is ignored and will be removed.

> [!IMPORTANT]  
> The minimum release computed for your submission also defines the availability in [!INCLUDE[prod_short](../includes/prod_short.md)] of all the extensions in your submission.
>
> For example, if the minimum release computed is 18.1, your extensions will be available starting from release 18.1.

> [!NOTE]  
> 30 days before the release of a new [!INCLUDE[prod_short](../includes/prod_short.md)] major version, all submissions are validated against the upcoming release. The apps in your submission must then be compatible with the upcoming release. The goal is to ensure that your customers won't be blocked during the upgrade of their environment.

### Against which countries/regions are my apps validated?

The extensions in your submission are validated for all the countries/regions targeted by the submission, which are available in [!INCLUDE[prod_short](../includes/prod_short.md)]. You can see which countries/regions you've selected in Partner Center under `Availability > Edit Markets`. 

When you're adding new localizations in [!INCLUDE[prod_short](../includes/prod_short.md)], these countries/regions can be added to Partner Center before they're ready in [!INCLUDE[prod_short](../includes/prod_short.md)]. If you're targeting a country/region marked as 'Planned' in [Country/regional availability](../compliance/apptest-countries-and-translations.md), depending on when your submission is processed, your apps might not be uploaded to [!INCLUDE[prod_short](../includes/prod_short.md)] if the localization isn't yet ready in [!INCLUDE[prod_short](../includes/prod_short.md)]. Generally, it's possible to upload apps for 'Planned' localizations a few weeks before they're officially released. When the localization becomes available, if you're experiencing issues installing your apps, you should increase the version in the app.json and submit the packages again in Partner Center. If you're using Azure Application Insights, you can check whether the country/region was validated using this [Troubleshooting Guide (TSG)](https://go.microsoft.com/fwlink/?linkid=2172328).

### Against which baselines are my apps validated?

The service will verify that your extensions don't introduce breaking changes by comparing them to the latest version available in AppSource for each country validated.

You can know which versions of your extensions were used as baseline during the breaking change validation by enabling Azure Application Insights in your extension and running this [Troubleshooting Guide (TSG)](https://go.microsoft.com/fwlink/?linkid=2172328).

> [!IMPORTANT]  
> As soon as your app has been uploaded to the AppSource marketplace, it will be used as a baseline during the technical validation of your next submissions. As a consequence, you won't be allowed to perform breaking changes without obsoleting the AL objects first and you won't be allowed to perform schema breaking changes; breaking changes on tables or table extensions. This applies also if your extension isn't used by customers yet. You should then not submit your app to the AppSource marketplace if you are still developing it and expect to change it in the near future.

### Which apps are validated in my submission?

The main app and the libraries required by the main app are validated and uploaded to [!INCLUDE[prod_short](../includes/prod_short.md)]. If you have included libraries, which aren't required by the main app, they'll be ignored during the validation and won't be uploaded to the service.

For example, let's consider an app A, which has an offer in the AppSource marketplace and A depends on a library named B, which doesn't have any dependencies. If you create a new submission with A as the main app and include B, C, and D as libraries, then only A and B will be validated. C and D will be ignored because they aren't required by the main app A. If B is updated to depend on C and D, then all apps in the submission will now be validated by the service.

> [!NOTE]  
> If some apps in your submission already have been uploaded to [!INCLUDE[prod_short](../includes/prod_short.md)] with the same version for some countries/regions, then the app will not be validated again for these countries/regions.

> [!IMPORTANT]
> If one or more libraries in your submission have their own offer, their listing(s) in the AppSource marketplace won't be updated automatically. In order to keep the listing(s) in sync with the version of the app(s) uploaded to [!INCLUDE[prod_short](../includes/prod_short.md)], you should submit a submission for their related offer(s).

### How long does the 'Automated application validation' take?

During 'Automated application validation', the apps in your submission are validated for each of the country/regions and each of the releases of [!INCLUDE[prod_short](../includes/prod_short.md)] targeted. If you already have a version of these extensions published to AppSource, then it will also run the breaking change validation using the apps currently in AppSource as baseline. Depending on the size of your app, the validation time can vary. Submissions are processed within a few minutes and we expect all submissions to be processed under 3 hours. However, if your app contains thousands of AL files, this process can take longer. We would then recommend splitting the app in smaller modules as it would also improve the development experience and the maintainability of your code base.

### How many automated tests do we need to run for validation and how high must the test coverage be?  

When setting up your offer in Partner Center, you must still include a test package in 'App Tests Automation', but it isn't used during the validation of the submission.

Test automation is something we expect you to run, to test your app and to make sure that the quality of your app is high. We don't run tests of your apps, nor do we have a set value for a required code coverage. Instead, we rely on you to test your app properly to give your customers a good experience.

### When I submit an app to AppSource; do you always make a manual validation based on the provided 'Key Usage Scenario' document?  

When setting up your offer in Partner Center, you must still include a document in 'Key Usage Scenario', but it isn't used during the validation of the submission.

We don't run a manual validation of the apps anymore. Instead, we rely on you to test that your app provides your customers with a good experience.

### When are my apps ready to be installed in my Business Central environment?

Shortly after the offer publishing process has been completed in Partner Center, your extensions will be available for installation in [!INCLUDE[prod_short](../includes/prod_short.md)].

[!INCLUDE[prod_short](../includes/prod_short.md)] currently doesn't support installing offers at the "Preview creation" step.

### When should I include my library apps as part of my submission?

You aren't required to always include the dependencies of your extension as part of your submission.

You're only required to include the dependencies for your extension as part of your submission if you're submitting a newer version for them. If you don't include them in your submission, they'll be downloaded automatically if they're available in [!INCLUDE[prod_short](../includes/prod_short.md)] for the targeted countries/regions.

> [!NOTE]  
> If you include the dependencies of your extension as part of the submission, these dependency versions will be used during the validation, even if there are higher versions already available in [!INCLUDE[prod_short](../includes/prod_short.md)].

If you didn't include the dependencies for your app and they aren't available, your submission will fail during the "Automated Application Validation" stage. Failing to find the dependencies for an extension results in error messages with the diagnostic codes `AVS0005` or `AVS0101`.

If you receive an error with the diagnostic code `AVS0107` and a message similar to `The extension 'MyApp' by 'MyPublisher' (version '1.2.3.4') has already been uploaded to Business Central for the country/region 'US'` for one of your library apps, it means that you've already published another .app file for this extension to [!INCLUDE[prod_short](../includes/prod_short.md)] as part of a previous submission. This can happen if you submit a .app file with different content, or created by a different build (each .app file created has a specific build ID stamped, so building multiple times the same project results in .app files with different build IDs). If this version of the library is already available for all countries/regions targeted by your submission, you can just remove the extension from the submission. If you're making your library available in new countries/regions, you should use the .app file that has already been uploaded to [!INCLUDE[prod_short](../includes/prod_short.md)] or increase the version number in the manifest of the extension (the app.json file).

### My app failed at the "Automated application validation" stage, what do I do next?

At this stage, your extensions are validated to assess whether they meet the requirements specified in the [Technical Validation Checklist](devenv-checklist-submission.md).

If this stage failed with an error message similar to `The validation of the submission failed for X out of Y tasks`, you must investigate what has caused the error. If you're using Azure Application Insights, information about the validation results is logged in Azure Application Insights. You can also use this [Troubleshooting Guide (TSG)](https://go.microsoft.com/fwlink/?linkid=2172328) in order to get started. If you're experiencing issues with Azure Application Insights, refer to the dedicated section below.

If this stage failed with an error message similar to `The extension 'MyApp' by 'MyPublisher' (version '1.2.3.4') has already been uploaded to Business Central for the country/region 'US'`, you must update the list of extensions submitted. For more information, see "When should I include my library apps as part of my submission?".

If this stage failed with an error message similar to `The manifest property 'X' of the extension 'My App' by 'Publisher Name' (version '1.2.3.4') specifies 'Y' while the offer description specifies 'Z'.`, you should either change your app.json file or the offer description to match each other and submit a new version. Offer description changes in Partner Center can be made in the "Properties" section of your offer for the app version, "Offer listing" section for the app name, and your publisher name can be found in Partner Center under `Account Settings > Organizational Profile > Legal > Developer > Publisher Name`. When changing any of these, remember to consult the section on this page called "Questions about app identity".

If this stage failed with an error message similar to `The submission must target at least one existing country/region of Business Central`, your submission doesn't target any countries/regions currently available in [!INCLUDE[prod_short](../includes/prod_short.md)]. If your submission targets a country/region marked as 'Planned' in [Country/regional availability](../compliance/apptest-countries-and-translations.md), you must wait for the localization to become available in [!INCLUDE[prod_short](../includes/prod_short.md)] and resubmit your offer. Generally, it's possible to upload apps for new localizations, a few weeks before they're made available to customers.

If this stage failed with an error message similar to `The extension 'MyApp' by 'MyPublisher' (version '1.2.3.4') contains inconsistent information about the package id/name/publisher/version`, it means that something went wrong when the package included in your submission was built. In order to mitigate the issue, you must rebuild the package and submit it again.

If this stage failed with an error message similar to `The App ID '<some-Guid>' is already used for Per-Tenant-Extensions in Business Central and cannot be used for the AppSource extension with name 'MyApp' and publisher 'MyPublisher'`, this means that there exists one or many PTEs with the same App ID in the service. Since [!INCLUDE[prod_short](../includes/prod_short.md)] doesn't support having AppSource apps and PTEs with the same App ID, it's then recommended to change the ID of your extension before submitting it in Partner Center. For more information, see [Moving a PTE to AppSource](devenv-extension-moving-scope.md#moving-a-pte-to-appsource). If the PTEs with that App ID aren't used in any customer environments anymore, you can create a support case in Partner Center to request an exception.

If this stage failed with an error message similar to `The extension 'MyApp' by 'MyPublisher' (version '1.2.3.4') has not been signed.` or `The extension 'MyApp' by 'MyPublisher' (version '1.2.3.4') has been signed, but the root certificate authority (CA) is not trusted.`, your submission doesn't live up to the code signing requirement of AppSource for [!INCLUDE[prod_short](../includes/prod_short.md)]. In order to correctly sign your app, please check out the section below called "Questions about code-signing validation" as well as [Sign an app package file](devenv-sign-extension.md).

If this stage failed with the following error message `Automated validation of the submission has failed. Please retry the operation and contact Partner Center support if it fails again. `, you should create a new submission in Partner Center. If your submission fails again, you should create a support case in Partner Center as documented in this article.

> [!NOTE]
> Because the extensions in your submission are validated for each release and country/region targeted by the submissions, the validation results can be really verbose and cannot always be displayed in their full length in Partner Center. The error message will then end with `...(Truncated)`. If that happens for your submission, you should either enable Azure Application Insights in your extension, run the self-validation script, or fix the errors visible and iterate on your submission.

### My app failed at the "Certification" stage, what do I do next?

At this stage, your extensions are validated to assess whether they meet the requirements defined in the [Marketing Validation Checklist](readiness/readiness-checklist-marketing.md).

Review the Marketing requirements and the [Marketing Validation FAQ](readiness/readiness-marketing-validation-faq.md) in order to fix the errors reported.

### My app failed at the "Publish application with the service" stage, what do I do next?

At this stage, your extensions are being published to [!INCLUDE[prod_short](../includes/prod_short.md)].

If this stage failed with the following error message `Automated upload to Business Central of the extensions in the submission has failed. Please retry the operation and contact Partner Center support if it fails again.`, you should create a new submission in Partner Center. If it fails again, you should create a support case in Partner Center as documented in the dedicated section below.

### My app failed at another stage, what do I do next?

If your submission failed at another stage than "Automated application validation", "Certification", or "Publish application with the service", you should create a support case in Partner Center as documented in the dedicated section below.

## Questions about hotfixing an AppSource app

For questions like what is qualified as a hotfix submission or what kind of changes can't be part of a hotfix, see [Hotfixing an AppSource app](devenv-hotfixing-appsource-app.md)

<!--
We're defining as `hotfix` the submission of a new version of an AppSource extension which will not become the latest version available in AppSource. 

For example, if you have version 2.0.0.0 of your extension available in AppSource, and you submit a new version 1.5.0.0, then version 1.5.0.0 is considered a hotfix because 1.5.0.0 will not become the latest version available.

> [!Important]  
> When submitting a hotfix, you must not update the version of your offer in Partner Center to match the hotfix version submitted, because the version in Partner Center is shown on the AppSource marketplace listing, which is meant to show the latest version.

> [!Note]  
> The concept of hotfix is tied to the country/region for which your apps version are available. If you have different versions of your apps on some countries/regions, your submission might be a hotfix for one country, but not for another one. However, we generally do not recommend having different versions per country.

### Against which releases is a hotfix submission validated?

When submitting a hotfix of your AppSource extension, the service will automatically detect the next version available and for which release of Business Central it's available. The service will then validate your submission up to that release. The minimum release targeted by the submission is computed based on the `application` property similarly to any other submission.

For example, if you have version 2.0.0.0 of your extension available in AppSource targeting Business Central version 21.0, and you submit a new version 1.5.0.0 with `application` set to 19.0.0.0, then version 1.5.0.0 will be validated for all Business Central releases from 19.0.0.0 (included) to 21.0.0.0 (excluded).

### What is the additional validation done for a hotfix submission?

In order to make sure your customer can upgrade from your hotfix version to the next version available in AppSource, we're validating the next version of your extension for breaking changes with your hotfix version.

For example, if you have versions 1.0.0.0 and 2.0.0.0 of your app in AppSource, and you submit a new version 1.5.0.0, the technical validation will verify that:
- there are no breaking changes between 1.0.0.0 and 1.5.0.0,
- there are no breaking changes between 1.5.0.0 and 2.0.0.0.

### What kind of changes can't be part of a hotfix?

Since the AppSourceCop will validate for breaking change the next version of your extension against the version you have submitted, you can modify the content of your procedure, but you can't add new AL objects or new elements (procedure, actions, fields, etc) to your extension's public API unless they are also part of the next version, or obsolete pending (except for table and table fields).

For example, let's consider that you have versions 1.0.0.0 and 2.0.0.0 of your app in AppSource.

Version 1.0.0.0 of your extension is defined as follows:
```al
codeunit 1000000 MyCodeunit
{
    procedure MyPublicProcedureFromV1()
    begin
    end;
}
```

Version 2.0.0.0 of your extension is defined as follows:
```al
codeunit 1000000 MyCodeunit
{
    procedure MyPublicProcedureFromV1()
    begin
    end;

    procedure MyPublicProcedureFromV2()
    begin
    end;
}
```

If you submit a new version 1.5.0.0, you're then allowed to add the following procedures:
- `local procedure MyNewLocalProcedure()` because it's not public,
- `[Obsolete] procedure MyNewObsoleteProcedure()` because it's obsolete pending,
- `MyPublicProcedureFromV2()` because it's already defined in the next version.

However, you're not allowed to define a new procedure `procedure MyNewPublicProcedure()`, because the service will detect that upgrading from version to 1.5.0.0 to version 2.0.0.0 results in the deletion of a public procedure. -->

## Questions about Azure Application Insights usage during AppSource submissions

### How do I enable Application Insights telemetry for my submissions?

To enable Application Insights signals for your submissions, you must specify the `applicationInsightsConnectionString` property in the manifest (app.json) of your extension. For more information about this property, see [JSON files](devenv-json-files.md).

### I don't see any signals in the resource specified for my extension, what do I do next?

Here's a list of steps that you can follow to troubleshoot this issue:

1. Validate that the Application Insights resource queried is the same one as specified in the manifest (app.json) of your extension.
2. Validate that the time range when running the query covers the time of the submission.
3. If you're using the `applicationInsightsKey` property in the manifest (app.json) of your extension, you should use the `applicationInsightsConnectionString` property instead because it's more reliable. Make sure to use the full connection string from your Azure Application Resource.
4. If you're using the `applicationInsightsConnectionString` property in the manifest (app.json) of your extension, make sure that you're using the full connection string and that it contains, at least, the following key-value pairs: `InstrumentationKey=<some-key>`, `IngestionEndpoint=<some-url>`, and `LiveEndpoint=<some-url>`. For more information, see [Connection strings](/azure/azure-monitor/app/sdk-connection-string)
5. Validate the data sampling and daily cap set for the Azure Application Insights resource. Navigate to the resource in Azure and go to 'Configure > Usage and estimated costs'. Validate that your Application Insights retains all data (data sampling is set to 100%) and that you haven't reached your daily cap. For more information, see [Sampling in Application Insights](/azure/azure-monitor/app/sampling). 

### I can see some signals in Application Insights, but I can't find why my submission failed, what do I do next?

Much information is provided in the custom dimensions of the signals. The validation errors can generally be found for the signals with eventId `LC0034`. For more information about the signals emitted during the technical validation of AppSource submission, see [Analyzing AppSource Submission Validation Trace Telemetry](../administration/telemetry-appsource-submission-validation-trace.md).

> [!NOTE]
> Instead of writing your own queries, we recommend using the executable Azure Data Studio [Troubleshooting Guide (TSG)](https://go.microsoft.com/fwlink/?linkid=2172328). This guide contains queries that will process the signals for your submission and extract the important information.

## Questions about developing and maintaining AppSource apps

This section contains frequently asked questions regarding developing apps (in Docker or SaaS). Fore information, about maintaining apps after they've reached the AppSource marketplace, see [Update Lifecycle for AppSource Apps FAQ](devenv-update-app-life-cycle-faq.md).

### What does it mean if I have an app in development that needs another dependency loaded, but I can't get the dependency's codeunits to load in my BC docker instance because it says the dependency's range is outside my range?

It means that your license doesn't allow you to publish that application. A recommendation would be to either get a runtime package from the developer of that AppSource app, which will allow you to bypass the licensing check or to try to test it on an online sandbox environment where that AppSource app is already installed. 

## Questions about code-signing validation

This section contains frequently asked questions related to the code-signing requirement from the [Technical Validation Checklist](devenv-checklist-submission.md). For more information about code-signing, see [Sign an APP Package File](devenv-sign-extension.md).

### Can I use any computer to sign my apps?

No, you need to use a Microsoft Windows computer that has [!INCLUDE[d365fin_long_md](includes/d365fin_long_md.md)] installed.

If [!INCLUDE[d365fin_long_md](includes/d365fin_long_md.md)] is not installed, you'll get an error similar to: "This file format cannot be signed because it is not recognized".

### Can I use a self-signed certificate to sign my apps targeting AppSource?

No, it isn't allowed to use a self-signed certificate. The .app package file must be signed using a certificate purchased from a Certification Authority that has its root certificates in Microsoft Windows. You can obtain a certificate from a range of certificate providers, including but not limited to GoDaddy, DigiCert, and Symantec.

### Do I need to use an EV code-signing certificate to pass the technical validation?

No, it isn't required to use an EV code-signing certificate. Standard code-signing certificates can be used to satisfy the code-signing requirement.

### Can I reuse the same code-signing certificate to sign multiple apps?

Yes, you can reuse the same code-signing certificate for multiple extensions. Code-signing certificates have a validity period defined over time.

### Which certificate format is accepted?
Currently we only accept `.pfx` certificates. However, if you have a different certificate format, check with your certificate provider to provide you `.pfx` file or convert your certificate to `.pfx`. There are resources online, which can help you convert a certificate to `.pfx` format.

## Questions about names, affixes, and ID ranges

In the following, you can read about how affixes and ID ranges are assigned.

### Do I need to register different affixes for each of my extensions?

No, you don't need to register affixes for each of your extensions.

The object affixes are registered per publisher so if your apps all have the same publisher, they can share the same affixes. The automated validation verifies that you're using the three letter affix registered by Microsoft in your extension, but this still allows you to create longer affixes per extension. For example, if you registered ABC as your affix, you can use ABCD as the prefix in Extension 1 and ABCE as the prefix in Extension 2. For more information, see [Prefix and suffix for naming in extensions](../compliance/apptest-prefix-suffix.md).

### Do I need to request a different ID range for each of my extensions?

No, you don't need to request a new ID range for each of your extensions.

The object IDs are registered per partner, not per extension. You can then use a subset of this range for each of your extensions. It is your responsibility to ensure that you aren't defining objects with the same IDs in different extensions. If you're doing so, the extensions defining these objects can't be installed together on the same environment. For more information, see [Get Started Building Apps](readiness/get-started.md#requesting-an-object-range).

### Will there be any changes made to the object names character limitation (30 characters) within the near future? 

We would like longer names as well. Introducing namespaces could be one investment. However, such a change has down-stream breaking impact (any caller needs to qualify calls) and there are SQL constraints on name lengths for tables, which currently include company name, table name, app ID and needs to be maximum 255. This is on our long term backlog, but haven't any changes planned soon.

## Questions about app identity

This section contains questions related to the identity of apps in AppSource. For more information, see the questions in [App Identity](devenv-app-identity.md).

### When is it okay to change the name of my extension?

Starting from [!INCLUDE[prod_short](../includes/prod_short.md)] 2021 release wave 2 (version 19.0), it's possible to change the name of your extensions without breaking dependent extensions.

When renaming an extension, you must:

- increment the version number in the manifest of your extension,
- make sure that your submission only targets releases of [!INCLUDE[prod_short](../includes/prod_short.md)] starting from 19.0.
- update the name of your offer in Partner Center - if your extension is the one for which the offer is created.

### When is it okay to change the publisher of my extension?

Starting from [!INCLUDE[prod_short](../includes/prod_short.md)] 2021 release wave 2 (version 19.0), it's possible to change the publisher name of your extensions without breaking dependent extensions.

When changing the publisher of an extension, you must:

- increment the version number in the manifest of your extension,
- make sure that your submission only targets releases of [!INCLUDE[prod_short](../includes/prod_short.md)] starting from 19.0,
- contact d365val@microsoft.com in order to register your affixes to your new publisher name.

### When is it okay to change the App ID of my extension?

> [!IMPORTANT]  
> The App ID is a critical part of the identity of apps in [!INCLUDE[prod_short](../includes/prod_short.md)], and changing it is a breaking change for all extensions depending on it. You should then not change the App ID of extensions which are installed for customers in Business Central Online.

If you are submitting a new version of your extension with a different App ID for an existing offer, then this new version will be considered as a different extension. This means that all extensions that depend on the extension with the old app ID must be updated to reference the new App ID. If they are not updated, this will cause issues such as customer environment upgrade failures which must be fixed within the required time period, see [Maintain AppSource Apps and Per-Tenant Extensions in Business Central Online](app-maintain.md). Since the app ID is part of how data is stored in [!INCLUDE[prod_short](../includes/prod_short.md)], this also means that you will have to migrate the data for all customers that have the extension with the old App ID installed. Note that we do not provide tools for performing data migration in SaaS, but you can create your own solution to export data from the old extension and re-import the data after the extension change.

### Is it possible to have multiple apps with the same App ID in AppSource? 

Each unique codebase has one unique ID. If you have four apps in AppSource, you need to have four unique IDs for these apps. Otherwise you'll get conflicts. 

### What if we already have an app on AppSource but we need to create the same app for another country; can we then have the same app ID for two different apps targeting two different countries/regions? 

If they're different apps (different code), they should have different identity. Identity is used in, for example, app management, dependencies, support cases, and telemetry. If reused across different apps, identity uniqueness is lost. Another approach could be a common shared (internal/library) app across countries/regions (with one app identity) and localized functionality as extensions on top (with their own identity). 

## Questions about Business Central offers

### When is it okay to change the offer type of my offer?

There exist two types of offers for [!INCLUDE[prod_short](../includes/prod_short.md)] in AppSource: `connect` apps and `add-on` apps. It's possible to change an offer type from `connect` to `add-on` by following the steps listed in the dedicated entry below. However, we don't recommend changing an offer from `add-on` to `connect` since it would be a breaking change for all other extensions depending on the apps in this offer.

For more information about the offer types for [!INCLUDE[prod_short](../includes/prod_short.md)], see [App type, contact type, and customer leads](readiness/readiness-checklist-e-industries-categories-apptype.md).

### How to change the offer type from 'connect' app to 'add-on' app?

When changing a `connect` app to an `add-on` app, you should:
- Navigate to your offer listing in the AppSource marketplace, and copy the URL for your offer
- Retrieve the App ID assigned by the service to your offer: the App ID can be found as `<appId>` in `https://appsource.microsoft.com/en-us/product/dynamics-365-business-central/PUBID.<publisherId>%7CAID.<offerId>%7CPAPPID.<appId>`
- Use this App ID in the `app.json` of the main extension uploaded to your offer

> [!NOTE]  
> The App ID is used as part of the URL of the offer listing and is used as a key to retrieve to customer review left on the offer listing. Not preserving the App ID means that the offer URL will change and customer reviews will be lost.

### How to automatically update my offer using Partner Center submission API?

It is possible to automatically submit apps to AppSource from our DevOps setup by using the [Partner Center Ingestion API](/azure/marketplace/azure-app-apis). For more information, you can also check this blog post [Automatic AppSource Submission of Business Central apps](https://freddysblog.com/2022/09/22/automatic-appsource-submission-of-business-central-apps).

## Channels to ask questions or report issues

In the following, you can read about how you reach out for support most efficiently.

### When do I contact d365val@microsoft.com?

When registering affixes for your publisher, or adding a new publisher name to your affixes. When contacting d365val@microsoft.com, make sure to provide the required information documented in [Benefits and Guidelines for using a Prefix or Suffix](../compliance/apptest-prefix-suffix.md).

### When do I contact Partner Center customer support?

When your submission fails to be successfully completed in Partner Center, but you're experiencing issues updating your extension(s) to fix the validation errors.

> [!IMPORTANT]  
> If you're using Azure Application Insights, before opening a support case for a failure at the 'Automated application validation', you must analyze the [signals](../administration/telemetry-appsource-submission-validation-trace.md) emitted in your Azure Application Insights storage. You can do so by using the [Troubleshooting Guide (TSG)](https://go.microsoft.com/fwlink/?linkid=2172328). When opening a support case, you must include the Kusto queries you used and the diagnostic messages that you found. Including the results from the TSG is also recommended.

### When do I contact Business Central customer support?

When your submission has been successfully completed in Partner Center, but your customers are experiencing issues installing or using the app.

### When do I log an issue on NavContainerHelper on GitHub?

When you have questions or bugs regarding the self-validation script, or any of the modules exposed by BcContainerHelper.

For more information, see [https://github.com/microsoft/navcontainerhelper/issues](https://github.com/microsoft/navcontainerhelper/issues).

### When do I write on Yammer?

When you have questions on developing and maintaining AppSource apps, on automatically submitting apps to AppSource, or about the validation process, you can ask a question on Yammer. In this group, you'll find announcements from Microsoft together with discussions around various AppSource-related articles.

You can join this AppSource group at [aka.ms/BCYammer](https://aka.ms/bcyammer) (note that you need to be a Microsoft partner to do so). If you have problems connecting, email dyn365bep@microsoft.com. 

## See also

[Technical Validation Checklist](devenv-checklist-submission.md)
