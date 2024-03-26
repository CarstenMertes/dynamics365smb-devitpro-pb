---
title: App type, contact type, and customer leads
description: Guidelines on app type, contact type, and customer leads.
author: a-emniel
ms.custom: na
ms.date: 02/08/2024
ms.reviewer: solsen
ms.topic: conceptual
---

# App type, contact type, and customer leads

## App type

| Type of app| Description |
|-------------|--------------|
|Add-on app | An add-on app extends the experience and the existing functionality of Microsoft Dynamics 365 Business Central. Add-on apps can be used in multiple scenarios, whether it's integrating to online services, making custom web services, adding business functionality, or extending the user interface. An add-on app can be a standalone app or an app with dependencies. Dependent add-on apps will automatically be installed together with your app. |
Connect app | A connect app is used in the scenario where there must be established a point-to-point connection between Business Central and a third party solution or service. With connect apps, data and app functionality lives in a service outside Business Central. The listing type of connect apps is always ‘Contact Me’, as they require external setup to work. Note: If your app can't integrate with Business Central through API, or require substantial coding in AL, the app should instead be submitted as an add-on app.

## Listing type

For add-on apps you must specify a listing type, whereas for connect apps the listing type is always “contact me”.  

|Listing type | Description | Button in AppSource | 
|-----------|--------------|--------------|
|'Get it now (Free)'|Provide your offer to customers for free. Choose this listing type, if you want to submit an entry or freemium app to AppSource. Note that freemium apps can offer an option to make the customer purchase extra functionality in the app, however it's a requirement that the app contains useful basic functionality that remains free. | A 'Get It Now' button will appear on your offer's storefront. 
|'Free Trial'| Customers can either try your offer for a short period of time, a limited number of users, or a limited number of transactions. When the trial period is over, the app will require payment. Choose this listing type when your reselling partner doesn't need extra assistance from you to install your app in the customer’s Business Central environment. That way, your reselling partners can easily roll out your app to multiple customers and scale your business. Note that you must allow the user to uninstall the app at no cost at the end of the trial period.|A 'Free Trial' button will appear on your offer’s storefront. 
|'Contact Me' | Let customers share their contact information with you via your lead management system. ‘Contact Me’ is for apps that require special attention, for example apps that require extra external setup or apps that shouldn't be used without proper guidance. Note that ‘Contact Me’ isn't a licensing option, because customers can install the app using the app ID defined in the manifest ([app.json](../devenv-json-files.md#appjson-file)) of the app, either in the [admin center API](/dynamics365/business-central/dev-itpro/administration/administration-center-api), or via direct URL `(https://businesscentral.dynamics.com/[TenantID]/?noSignUpCheck=1&filter=%27ID%27%20IS%20%27[AppID]%27&page=2503)` (where [TenantID] is the Microsoft Entra ID of their environment, and [AppID] is the app ID defined in the manifest of the main extension for this offer). In the AppSource marketplace, the customer will be asked to share their information with Microsoft through your customer relationship management (CRM) system. These customer details, along with the offer name, ID, and marketplace source will be sent to the CRM system, which you've configured. You can then share the installation URL for your extension to the customer. Note that ‘Contact Me’ generally isn't a recommended solution, because it'll affect your ability to scale. Instead, we recommend that you build monetization into your offer and use ‘Free trial’, as it gives your prospective customers an easy option to try out and test your app. Furthermore, this contact type shouldn't be used to generate leads, instead use the possibility of creating consulting services.  | A 'Contact Me' button will appear on your offer's storefront.|

> [!NOTE]  
> Microsoft recommends that add-on apps are listed as 'Free’ or ‘Free Trial’. It's possible to switch listing type as your app matures.  

## Customer leads

Provide connection details to the CRM system where you would like us to send customer leads. Read more about configuring customer leads
[here](/azure/marketplace/partner-center-portal/commercial-marketplace-get-customer-leads#connect-to-your-crm-system).
