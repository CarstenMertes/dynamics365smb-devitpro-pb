---
title: "Lifecycle of apps and extensions FAQ"
description: "Overview of the frequently asked questions about updating an app on AppSource."
author: SusanneWindfeldPedersen
ms.topic: conceptual
ms.author: freddyk
ms.date: 08/01/2021
ms.reviewer: jswymer
---

# Update lifecycle for AppSource apps FAQ

See the following sections for frequently asked questions regarding updating apps on AppSource.

## I want to submit an updated version of my app. What is the process for that?
For any updated version of your app (small or large changes), you follow the same submission as your original version. It must go through the same validation process. The following are the steps that you must follow:
- Increase the version number of your app within its json/manifest file.
- Don't change the app’s AppID within its json/manifest file. That needs to remain the same for life of the app
- Include an upgrade codeunit and ensure that it works. 
- Upload the app file to your existing Partner Center offer.
- In Partner Center, edit the version field to match what is now in your updated app file.
- Make any other edits in Partner Center as needed.
- Submit for validation.
- Validation takes place as normal (against current production version of Business Central at time of submission):
    - Code review is needed for avoiding violations and ensuring requirements are met.
    - Test validation is scaled back for updated versions.

## What happens when my updated app passes validation?
The app is checked into our service and becomes the active version for that current production release of Business Central. If a tenant is already upgraded to the current release, they can install this updated version of your app.

## Does Microsoft now update my app (to this latest updated version) on all tenants that already have a previous version?
Microsoft will only force update apps during the 2 major releases (release wave 1 and 2). For these releases, each tenant will have their AppSource apps force updated to the latest available versions in our service.

## How do I update the apps on my tenant for minor releases then?
If a tenant wants to update the apps on their tenant during the minor releases, the tenant admin needs to handle this. Here are the steps you follow to update your apps:
- Sign in to your Business Central Web client instance.
- Navigate to the **Extension Management** page.
- Find the app and uninstall it.
- Reinstall the app.

That gives you the latest available version in our service.

> [!NOTE]  
> If a per-tenant extension contains breaking changes, it is possible to force an update by using the **Force** option on the **Extension Management** page. For more information, see [Uploading a Per-Tenant Extension (PTE)](/dynamics365/business-central/ui-extensions-install-uninstall).

## How often should I submit updates of my app?
Our recommendation is to pack more bug fixes and features into less frequent updates. Try to avoid frequent submissions containing very few changes. Being on a more frequent cadence than Business Central (monthly) isn't advised. This leads to lower churn to production tenants.

## What if a customer reports a critical bug in my app and needs an immediate hotfix version of my app?
We have automated many things and most of the submissions are now processed within one business day. The technical validation of the app is fully automated so you'll know within a few minutes (hours in the worst case) if your app passed the validation or not. Once your app has passed the certification stage, it's automatically published to [!INCLUDE[prod_short](../includes/prod_short.md)] and becomes available for your customers. 

Before submitting your apps in Partner Center, our recommendation is to make sure you fulfilled all the requirements in the technical validation checklist, including running the self-validation.

## Do you have any tips for us when submitting updates of our app?
Yes, we have some valuable tips we would like to share. These are tips that can save you time in the validation process. They'll help lead to fewer (and possibly zero) failures during validation. Most importantly; they'll lead to fewer issues being found in production by customers.

- Follow the checklist, for more information, see [Technical Validation Checklist](devenv-checklist-submission.md). The checklist is ever evolving and requirements might change or be added. You might miss something from the checklist, leading to validation failure and delaying the passing of your updated app.
- Follow the technical validation FAQ, for more information, see [Technical Validation FAQ](devenv-checklist-submission-faq.md). We're regularly updating it based on the questions and support cases raised by partners.
- Use AppSourceCop, for more information, see [Using the Code Analysis Tool](devenv-using-code-analysis-tool.md). This helps to catch any missing prefix/suffix and DataClassification. Too often we see these fail the updated versions of apps.
- Sign your app. This fails many app validations. We try to publish the app during validation and it isn't properly code-signed leading to failure to publish.
- Publish and install your app. This is another significant validation failure we see too often.
- Test your app’s functionality with 100% coverage. You're the expert on the app and know it best. If you're only testing a small percentage of your app, customers will most likely find issues resulting in you having to update your app more often. And if customers are the ones finding your app issues, they might decide to uninstall it. You should have a vested interest in providing a quality app.
- Test the upgrade of your app. upgrade from the previous version to this latest. Your updated app won't pass validation until the upgrade works. If it fails in our validation, we'll return it to you, leading to a delay in it going to our service.
- [!INCLUDE[appsource-appinsights](includes/appsource-appinsights.md)].
 
> [!NOTE]  
> The tips that we provide above are for your benefit to pass validation the first time through each submission. And to emphasize these points, think of the delays that can arise when you don't follow these tips. If you submit, it can take a couple days before we validate the app. Once we validate it, if all is good, it should pass quickly. If we find issues that lead us to fail the validation, we send the app back to you as you have to make fixes. It could then take you days to properly fix. Next time you submit, your app does not go to the front of the queue. It begins at the bottom again which means it could be another couple days before we validate it again. By following our tips above, you can avoid those delays. Spend a bit more time up front finding those issues yourself, leading to a quicker path to our service.

## Related information
[Retaining table data after publishing](devenv-retaining-data-after-publishing.md)  
[Checklist for Submitting Your App](devenv-checklist-submission.md)  
[Upgrading Extensions](devenv-upgrading-extensions.md)  
[Using the Code Analysis Tool](devenv-using-code-analysis-tool.md)  
