---
title: "FAQ about Testing your Business Central App"
description: "Get answers to some of your questions about testing when you build an app for Dynamics 365 Business Central"
author: freddyk
ms.date: 08/15/2022
ms.reviewer: jswymer
ms.topic: faq
ms.author: freddyk
---

# FAQ about Testing your Business Central App

This section contains answers to frequently asked questions about testing your app when you submit an app for [!INCLUDE[prod_short](../includes/prod_short.md)].

## Since my app goes through validation, do I really need to thoroughly test my app?

Yes. It's your app and you're the expert, so you should have a vested interest in high quality. The main goal of validation is to ensure app code is meeting requirements and policy. The testing done during validation is only to ensure good user experience on the most common app scenarios. We don't test every scenario of an app. Using customers to find bugs isn't the proper approach.

## Is it ok to submit my app for validation before we complete our own testing?

No. Please, don't submit your app for validation until it has been 100% tested. This will lead to many delays in the validation process otherwise. Also, it wastes time and resources.

## Is it ok to test my AppSource app in an on-premises environment?

No. You must test your app using [!INCLUDE[prod_short](includes/prod_short.md)] online. Although [!INCLUDE[prod_short](includes/prod_short.md)] online and on-premises are similar, they aren't the exact same. If you only test on-premises, invariably issues will be found in our validation testing.

## Does it really matter what version of Business Central I test on before submitting my app for validation?

Yes. It's critical that you always test on the latest version at the time when you're ready to submit for validation. Testing on the wrong version usually leads to validation failure. For example, let’s say the latest version of [!INCLUDE[prod_short](includes/prod_short.md)] is 15.4 at the time when you submit for validation you tested on 15.0. The product has changed between those versions, and deprecated features or other changes could result in your app behavior changing.

We recommend that you consider using Docker containers. Use the `Get-BcArtifactUrl` function in the BCContainerHelper PowerShell module to give you the artifact URL for the latest sandbox build for the specified country. You don’t have to figure out what product version is active at time of submission. That function does it for you.

## How thorough should our testing be?

You should always test with 100% coverage, or at least as close to 100% as you can get. The testing should be a combination of automated and manual tests. The apps with good testing infrastructure behind them are the most successful.

## Do I have to test on every country that I intend to support with my app?

Yes. If you support multiple countries/regions, test your app on every country. Each country's code base is slightly different from both the base application and other countries/regions. It's critical to make sure that the app publishes, syncs, and installs on every country you support. Because an app installs fine on one country doesn’t mean it will publish/install fine on another. We have seen many times where it passes on one but fails on another during our validation.

## Do you have recommendations on maintenance testing of our apps?

Yes. You should be testing your apps against our various build branches. Through Docker, you have access to our latest sandbox builds and our latest next major and next minor insider builds - all are public. Test often, especially against the Next Minor build. This allows you to catch any bugs that may arise from core changes in the product.

## I only made minor code changes in my updated app. Can I test just these changes?

No. You should always test 100% coverage no matter what. Testing only what you changed isn't the correct approach. Even minor changes can lead to breaking changes where you least expect it.

## Do I need to do upgrade testing?

Yes, this is a must. If an app fails to upgrade, customers are unable to get your updated app. This is one of the common failures we see today in validations. You should want your app upgrade to work optimally.

## Any recommendations on upgrade testing?

Test the upgrade with extensive app data included. Many of the upgrade failures for customers are data related. The upgrade fails because specific data scenarios weren't considered for testing. Or worse, the upgrade succeeds, and data is lost.

## Do I only need to do upgrade testing from previous version to current?

No. It's important you test from various previous versions of your app. This is because we don't automatically upgrade apps for minor releases. You could have a tenant back on version 1.0.0.0 of your app and have to jump all the way to version 1.0.0.5. We don’t guarantee direct upgrades of apps from their most previous version.

## Related information

[FAQ about Updating your Business Central App](app-faq-update.md)  
[FAQ about Library & Dependency Apps in Business Central](app-faq-dependencies-libraries.md)  
[Update Lifecycle for AppSource Apps FAQ](devenv-update-app-life-cycle-faq.md)  
[The Lifecycle of Apps and Extensions for Business Central](devenv-app-life-cycle.md)  
