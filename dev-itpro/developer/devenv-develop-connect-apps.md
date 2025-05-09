---
title: Get started developing Connect apps for Dynamics 365 Business Central
description: Learn how to get started developing a Connect app 
author: SusanneWindfeldPedersen
ms.author: solsen
ms.date: 11/13/2024
ms.topic: get-started
ms.collection: get-started
ms.reviewer: solsen
---

# Get started developing Connect apps for [!INCLUDE [prod_long](includes/prod_long.md)]

[!INCLUDE[azure-ad-to-microsoft-entra-id](~/../shared-content/shared/azure-ad-to-microsoft-entra-id.md)]

A Connect app establishes a point-to-point connection between [!INCLUDE [prod_long](includes/prod_long.md)] and a third-party solution or service and is typically created using standard REST API to interchange data. Any coding language capable of calling REST APIs can be used to develop your Connect app. In the following section, you can read about how you get started exploring the available APIs for [!INCLUDE [prod_long](includes/prod_long.md)].

[![Shows the API stack in Business Central](media/api-stack.svg)](media/api-stack.svg#lightbox)

To explore and develop against REST APIs in [!INCLUDE [prod_long](includes/prod_long.md)], you must first sign up for a trial tenant, and then you must connect and authenticate. To do that, follow these steps:

1. Sign up for [Dynamics 365 Business Central](https://signup.microsoft.com/signup?sku=6a4a1628-9b9a-424d-bed5-4118f0ede3fd&ru=https%3A%2F%2Fbusinesscentral.dynamics.com%2FSandbox%2F%3FredirectedFromSignup%3D1).  
When you have your tenant, you can sign into the UI to explore the product and the [APIs](/dynamics-nav/api-reference/v2.0)
2. There are two different ways to connect to and authenticate against the APIs.  
    - Use Microsoft Entra ID based authentication against the common API endpoint: `https://api.businesscentral.dynamics.com/v2.0/<environment name>/api/v2.0`
    - Use basic authentication with username and password (a so-called web service access key) against the common API endpoint that includes the user domain, for example `https://api.businesscentral.dynamics.com/v2.0/production/cronus.com/api/v2.0`.  
        > [!IMPORTANT]  
        > When going into production, you should use Microsoft Entra/OAuth v2 authentication and the common endpoint `https://api.businesscentral.dynamics.com/v2.0/production/api/v2.0`. For exploring and initial development, you can use basic authentication.
        > [!IMPORTANT]  
        > Basic authentication is deprecated with Business Central 2022, release wave 1 for SaaS. Learn more in [Deprecated features in the platform - clients, server, and database](../upgrade/deprecated-features-platform.md#accesskeys).

To construct the URL for the environment, the path needs to contain the environment name. To learn how to get a list of environments deployed on the tenant, see [Getting a list of environments](../webservices/api-get-environments.md). OAuth is required for this endpoint. 

<!-- Learn more in the [Exploring the APIs with Postman and Microsoft Entra authentication](#explore-rest-apis-with-postman-and-microsoft-entra-authentication) section. -->

<!-- In the following sections you can read more about setting up the two types of authentication and using both authentication methods in Postman. -->

APIs can also be explored through the [OpenAPI specification for Business Central](/dynamics-nav/api-reference/v1.0/dynamics-open-api).


## Set up Microsoft Entra ID based authentication

Sign in to the [Azure portal](https://portal.azure.com) to register [!INCLUDE [prod_long](includes/prod_long.md)] as an app and thereby provide access to [!INCLUDE [prod_long](includes/prod_long.md)] for users in the directory.

1. Follow the instructions in the [Integrating applications with Microsoft Entra ID](/azure/active-directory/develop/quickstart-register-app) article. The next steps elaborate on some of the specific settings you must enable.
2. On the **API permissions** page for your app, select the **Add a permission** button. 
3. Make sure the **Microsoft APIs** tab is selected. In the *Commonly used Microsoft APIs* section, select **Dynamics 365 Business Central** and select **Delegated permissions**.  
4. Ensure that the right permission is checked: **Financials.ReadWrite.All**. Use the search box if necessary.
5. Choose the **Add permissions** button.
    > [!NOTE]  
    > If **Dynamics 365** doesn't show up in search, it's because the tenant doesn't have any knowledge of Dynamics 365. To make it visible, an easy way is to register for a [free trial](https://signup.microsoft.com/signup?sku=6a4a1628-9b9a-424d-bed5-4118f0ede3fd&ru=https%3A%2F%2Fbusinesscentral.dynamics.com%2FSandbox%2F%3FredirectedFromSignup%3D1) for [!INCLUDE [prod_long](includes/prod_long.md)] with a user from the directory. 

6. From the **Certificates & secrets** page, in the **Client secrets** section, choose **New client secret**:
    - Type a key description (of instance app secret),
    - Select a key duration of either **In 1 year**, **In 2 years**, or **Never Expires**.
    - When you select the **Add** button, the key value is displayed, then copy, and save the value in a safe location.

    > [!NOTE]  
    > You'll need this key later to configure the project in Visual Studio. This key value won't be displayed again, nor is it retrievable by any other means, so record it as soon as it's visible from the Azure portal.

You have now set up the Microsoft Entra ID based authentication. Next, you can go exploring the APIs. 

<!-- Learn more in the [Exploring the APIs with Postman and Microsoft Entra authentication](#explore-apis-with-postman-and-basic-authentication-only-for-on-premises) section. -->


## Set up basic authentication (only for on-premises)

[!INCLUDE[webservice_key_deprecated](../includes/web-service-key-deprecated.md)]

If you prefer to set up an environment with basic authentication just to explore the APIs, you can skip setting up the Microsoft Entra ID based authentication for now and proceed with the steps below. If you, however, want to go into production, you must use Microsoft Entra ID/Oauth v2 authentication, see the section [Setting up Microsoft Entra ID based authentication](#set-up-microsoft-entra-id-based-authentication).

1. To set up basic authentication, log into your tenant, and in the **Search** field, enter **Users** and then select the relevant link.
2. Select the user to add access for, and on the **User Card** page, in the **Web Service Access Key** field, generate a key.  
3. Copy the generated key and use it as the password for the username. 

Now that we have the username and password, we can connect and authenticate, which you can do from code, or API explorers such as Insomnia, Bruno, or Insomnium. <!-- In the [Exploring the APIs with Postman and basic authentication](#explore-apis-with-postman-and-basic-authentication-only-for-on-premises) section, we use Postman. -->

<!--
## Explore REST APIs with Postman and Microsoft Entra authentication

In this `Hello World` example, we're going over the basic steps required to retrieve the list of customers in our trial tenant. This example is based on running with Microsoft Entra authentication.

1. First, in Postman, set up a `GET` call to the base API URL.
    - When you call the base API URL, you get a list of all the available APIs. You can append `$metadata` to the URL to also get information about the fields in the APIs. The list of supported APIs and fields information can also be found in the API documentation, for example, call `GET https://api.businesscentral.dynamics.com/v2.0/environment name/api/v2.0`
2. On the **Authorization** tab in Postman, select **OAuth 2.0** in the **Type** and then choose **Get New Access Token**. 
3. In the **GET NEW ACCESS TOKEN** window, enter the following information as specified below:
    - In the **Token name** field, choose a descriptive name.
    - In the **Grant type** field, choose **Authorization Code**.
    - In the **Callback URL** field, specify the URL specified as the sign-on URL/Reply URL in the Azure portal.
    - In the **Auth URL** field, specify a URL such as `https://login.windows.net/<your tenant domain>/oauth2/authorize?resource=https://api.businesscentral.dynamics.com`.
    - In the **Access Token URL** field, specify a URL such as `https://login.windows.net/<your tenant domain>/oauth2/token?resource=https://api.businesscentral.dynamics.com`.
    - In the **Client ID** field, enter the Application ID from the registered app in Azure portal.
    - In the **Scope** field, 
    - In the **Client Secret** field, enter the key generated under **Keys** that you copied in step 6 in the [Setting up Microsoft Entra ID based authentication](#set-up-microsoft-entra-id-based-authentication).
    - In the **Client Authentication** field, choose the **Send client credentials in body** option.
4. Choose the **Get New Access Token** button. The first time you sign in, you get prompted for consent.
5. Scroll down and choose **Use token** button.  
An Authorization request header is now added containing the Bearer token.
6. Choose **Send** in Postman to execute the call, and inspect the returned body, which should include a list of the APIs.

## Explore APIs with Postman and basic authentication (only for on-premises)

In this `Hello World` example, we're going over the basic steps required to retrieve the list of customers in our trial tenant. This example is based on running with basic authentication. 

1. First, in Postman, set up a `GET` call to the base API URL.  
    - When you call the base API URL, you get a list of all the available APIs. You can append `$metadata` to the URL to also get information about the fields in the APIs. The list of supported APIs and fields information can also be found in the API documentation.

    - Since we're using basic authentication, we need to include the user's domain in the URL, for example, call `GET https://api.businesscentral.dynamics.com/v2.0/<your tenant domain>/<environment name>/api/v2.0`.
        > [!NOTE]  
        > The parameter `<your tenant domain>` is your default Microsoft Entra ID GUID.
    
2. On the **Authorization** tab in Postman, select **Basic Auth** in the **Type** and provide the Username and **Web Service Access Key** from above as password. 

3. Choose **Send** in Postman to execute the call, and inspect the returned body, which should include a list of the APIs.


## Call an API

Each resource is uniquely identified through an ID, see the following example of calling `GET <endpoint>/companies`:  

```json
    {
        "@odata.context": "<endpoint>/$metadata#companies",
        "value": [
            {
                "id": "a0a0a0a0-bbbb-cccc-dddd-e1e1e1e1e1e1",
                "systemVersion": "18453",
                "name": "CRONUS USA, Inc.",
                "displayName": "CRONUS USA, Inc.",
                "businessProfileId": ""
            }
        ]
    }
```

The resource ID must be provided in the URL when trying to read or modify a resource or any of its children. The ID is provided in parenthesis `()` after the API endpoint. For example, to GET the "CRONUS USA, Inc." company details, you must call `<endpoint>/companies(a0a0a0a0-bbbb-cccc-dddd-e1e1e1e1e1e1)/`.

All resources, such as customers, invoices etc., live in the context of a parent company, of which there can be more than one in the [!INCLUDE[d365fin_long_md](includes/prodlong.md)] tenant. Therefore, it's a requirement to provide the company ID in the URL for all resource API calls. To GET all customers in the "CRONUS USA, Inc." company, we must call a GET on the URL `<endpoint>/companies(a0a0a0a0-bbbb-cccc-dddd-e1e1e1e1e1e1)/customers`.
-->

## Related information

[API developer overview](devenv-api.md)
[Using filtering with APIs](devenv-connect-apps-filtering.md)  
[Tips for working with APIs](devenv-connect-apps-tips.md)   
[Troubleshooting API calls](../webservices/dynamics-error-codes.md)    
[API performance](../webservices/web-service-performance.md)   
