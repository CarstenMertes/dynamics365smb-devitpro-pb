---
title: Requirements for connectivity apps
description: Learn about connectivity apps, how they can increase business productivity, and how to get your app listed as a connectivity app.
ms.date: 05/23/2023
ms.topic: conceptual
author: sorenfriisalexandersen
ms.author: soalex
ms.reviewer: solsen
---

# Requirements for connectivity apps

To get a connectivity app listed in [!INCLUDE [prod_short](../includes/prod_short.md)] online, the app publisher must follow certain requirements and best practices. This article explains these requirements and how to apply to have your connectivity app included.

## What are connectivity apps?

In [!INCLUDE [prod_short](../includes/prod_short.md)] online, connectivity apps provide an easy and secure connection to external services, such as banks. this way, they can automate otherwise manual tasks, which improves business productivity. Connectivity apps as a feature are described here:

* [Connect to banks](/dynamics365/business-central/ui-extensions#connect-your-business) (starting in [!INCLUDE [prod_short](../includes/prod_short.md)] 2022 release wave 2)

## What connectivity app publishers need to know

Connectivity apps are AppSource apps for [!INCLUDE [prod_short](../includes/prod_short.md)] online built by independent software vendors (ISVs) to provide customers with a truly connected experience. Such apps connect [!INCLUDE [prod_short](../includes/prod_short.md)] to various types of external providers and bring relevant functionality to running a business in the cloud. The following list provides examples of types of apps that can boost productivity:

* Import bank transactions  
* Initiate payment transfers  
* Manage employee payroll  
* Send and receive electronic invoices  

Publishers of connectivity apps benefit from in-product visibility. They also have these responsibilities for their apps:

* Extra app compatibility requirements

    Publishers of connectivity apps must ensure continuous compatibility with the latest version of [!INCLUDE [prod_short](../includes/prod_short.md)], meaning they can be upgraded to the next minor and major version. Publishers must also be proactive in their approach to compatibility.

* Test coverage

    The connectivity app publisher also provides automated testing when they submit their app to AppSource. These tests must cover more than 85 percent of the app's functionality.

* Sales volume requirements

    Sales volume requirements ensure the app provider is constantly serving a critical mass of customers per listed country/region, and is continuously growing its customer base. The concrete sales volume requirements may change over time and for various markets.  

    Currently, an app is eligible for review to be included as a connectivity app on the following terms:

  * It has 10 paying customers in its primary country/region
  * The ISV commits to 25 paying customers in the country/region after a six months ramp-up period.  

    The six months ramp-up period starts at the date when the [!INCLUDE [prod_short](../includes/prod_short.md)] update that includes the app in the listing of connectivity apps is generally available.

* Providing best-in-class experiences

    The connectivity app council, consisting of Microsoft experts and best-in-class app publishers, have the following tasks:

  * Review the user experience of aspiring connectivity apps  

  * Run recurring reviews of existing connectivity apps experiences  

    The council comments on a submitted application's functionality, user experience, use of onboarding components, and other considerations that influence the customer experience with the app and the support experience. We expect the ISV to make the relevant changes, based on the guidance and feedback given by the council.  

* Functional app recommendations and requirements

    Publishers of connectivity apps are advised to follow these guidelines to get the best possible review from the connectivity apps council:

  * Use elements of the onboarding framework in your app.  

    Examples include an assisted setup that starts after the app completes the installation, or it can easily be found in the **Extensions Management** page. Use of teaching tips for education of the user, and so on. Learn more at [Onboarding Experiences](../administration/onboarding-experiences.md).
  * Include only the functionality that serves the core purpose of the app.  

    To that end, if your app brings banking connectivity, it shouldn't contain all other financial functionality that depends upon bank data. Stick to the core functionality and offer more functionality in other apps.
  * Have either a **get it now** or **free trial** call to action when published on AppSource.  

    No apps of requiring a customer to **contact me** is allowed.
  * For bank connectivity apps, provide connections to one or more banks. Make it easy for the [!INCLUDE [prod_short](../includes/prod_short.md)] user to retrieve account and transaction information and initiate single domestic payments.  

    Connections can be made directly to the banks’ API or through an aggregator of bank APIs. This seamless integration is key to a positive user experience.

* Regulatory compliance

    Connectivity apps must comply with local regulatory, security, and data protection requirements such as PSD2. In markets where PSD2 and similar regulation are used, it's the publisher's responsibility to ensure the necessary licenses are in place, such as account information service provider (AISP) and payment information service provider (PISP) licenses. Many aggregators of bank APIs offer an agent model where the app publisher is an agent of the aggregator and uses the aggregator's AISP or PISP licenses. If that's not possible, as when integrating directly with banks' APIs, it's necessary for the app publisher to provide the licenses. Failure to comply not only results in rejection from the connectivity apps list, but also rejection by AppSource.

## Get the app listed as a connectivity app

If you fulfill the requirements outlined, you can apply to get listed by sending an e-mail to [Business Central Connectivity Apps Requests](mailto:bc-connectivity-apps@microsoft.com).

Make sure you specify the following information:

* App ID
* App Name
* Publisher Name
* Publisher ID
* Connectivity type, such as *banking*  
* Country/region where you want your app to be listed

## How often is the list of connectivity apps updated?

ISVs may submit applications continuously, and quarterly reviews are scheduled. If an app fulfills the requirements to become a connectivity app, the ISV is notified immediately, and will coordinate with Microsoft for addition to the list at the earliest possible convenience.  

> [!NOTE]  
> The requirements to become a connectivity app as listed above may change over time. The changes will be reflected in this article, so make sure you follow the recommendations and requirements here to make sure your app complies with the current rules.

## See also

[Best Practices for AL](apptest-bestpracticesforalcode.md)  
[Onboarding experiences](../administration/onboarding-experiences.md)  
[Configure Context-Sensitive Help](../help/context-sensitive-help.md)  
