---
title: "App Management for ISVs"
description: The App Management API can help you manage your apps running in different customer Business Central environments.
author: jswymer
ms.custom: na
ms.date: 04/01/2021
ms.reviewer: na
ms.topic: overview
ms.author: jswymer
---

# App Management for ISVs

[!INCLUDE[2020_releasewave1](../../includes/2020_releasewave1.md)]

Each [!INCLUDE[prod_short](../../developer/includes/prod_short.md)] environment is built as a collection of apps. These apps include Microsoft apps and apps from AppSource that reselling partners have installed for customers. The apps are working together to provide customers with a broad set of features to address their various business, market, and industry needs.

As an authorized ISV, you can deliver your functionality or your services as apps in AppSource. For more information, see [Get Started with Building Apps](../../developer/readiness/get-started.md). To help you manage your apps running in different customer Business Central environments, [!INCLUDE[prod_short](../../developer/includes/prod_short.md)] provides the App Management API.

## About the App Management API

The App Management API is a REST-based API. It requires that you're an authorized ISV and your apps have been registered by Microsoft. Once registered, you access the API by using this global endpoint: [https://apps.businesscentral.dynamics.com](https://apps.businesscentral.dynamics.com). 

You can use the API for the following operations:

- Make major, minor, and hotfix app updates available to customers for installation from the Business Central administration center.

    You make the updates available by uploading them to the App Repository. The new app versions will then be available on [Manage Apps](../tenant-admin-center-manage-apps.md) page of the Business Central administration.
- Retrieve the list of the customers' environments that have your app installed.
- Schedule the automatic deployment of the app hotfixes for their customers' environments.  

The App Management API lets you apply modern continuous integration (CI), continuous deployment (CD), and DevOps practices to your work, for example:

- Automate operations by using [AL-Go for GitHub](https://aka.ms/AL-Go) .
- Organize role-based access control.
- Manage your apps at scale, in multiple geo locations, supported by advanced and well-controlled build, test, and release flows.

For more information about the API, see [App Management API](app-management-api.md).

> [!NOTE]
> Currently, direct access to the API is only available for the ISVs working with the Embed apps; not Add-on and Connect apps. To manage versions of Add-on and Connect apps, you use Partner Center to upload the new app versions to **Business Central** offers. The apps will undergo a technical and marketing validation before becoming available on AppSource. After passing validation, the new versions are made available in Business Central administration center to the customers that have these apps installed.

## Legal information

The apps that are stored in the App Repository are governed by the Microsoft Publisher Agreement. For more information, see [Publishing your business application](https://partner.microsoft.com/solutions/business-applications/isv-publish). 

The App Management API is governed by Microsoft APIs Terms of Use. For more information, see [Microsoft APIs Terms of Use](/legal/microsoft-apis/terms-of-use)  

## See Also

[Manage Apps in the Business Central Administration Center](../tenant-admin-center-manage-apps.md)   
