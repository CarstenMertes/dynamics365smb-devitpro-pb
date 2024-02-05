---
title: Register on-premises as an app in the Azure Management Portal
description: Learn what to do when you want to use Business Central on-premises with online offerings.
author: jswymer
ms.author: jswymer
ms.custom: bap-template
ms.date: 01/26/2023
ms.reviewer: na
ms.topic: how-to

---

# Register Business Central On-Premises in Microsoft Entra ID for Integrating with Other Services

> **APPLIES TO** [!INCLUDE [prod_short](../developer/includes/prod_short.md)] on-premises. [!INCLUDE [prod_short](../developer/includes/prod_short.md)] online is automatically configured for integration with other online services.

[!INCLUDE[azure-ad-to-microsoft-entra-id](~/../shared-content/shared/azure-ad-to-microsoft-entra-id.md)]

This article describes how to set up [!INCLUDE [prod_short](../developer/includes/prod_short.md)] on-premises to use services that are based on Microsoft Azure. There are several services that you can integrate with [!INCLUDE [prod_short](../developer/includes/prod_short.md)] on-premises, like Cortana Intelligence and Power BI. Before using the services, you have to register Business Central on-premises in Microsoft Entra ID and give it access to the services. For example, the [Sales and Inventory Forecast](/dynamics365/business-central/ui-extensions-sales-forecast) extension requires that you specify an API key and API URI. Other services require similar information.

> [!NOTE]
> In [!INCLUDE [prod_short](../developer/includes/prod_short.md)] version earlier than 16.4, the **Set up Microsoft Entra ID** wizard has an **Auto register** action. Previously, you could use this action to automatically register [!INCLUDE [prod_short](../developer/includes/prod_short.md)] in Microsoft Entra ID. The auto-register functionality has since been removed. Now, you must register the application manually, regardless of your version. The wizard in earlier versions still includes the **Auto register** link. But the link now opens this article, which guides you through the manual registration.

## Prerequisites

- A Microsoft Entra tenant.

   You need a tenant on Microsoft Entra ID that has at least one user. For more information, see [Quickstart: Set up a tenant](/azure/active-directory/develop/quickstart-create-new-tenant).

   If the [!INCLUDE [prod_short](../developer/includes/prod_short.md)] deployment is using Microsoft Entra authentication, then you already have a tenant with users. See [Authenticating [!INCLUDE[prod_short](../developer/includes/prod_short.md)] Users with Microsoft Entra ID](authenticating-users-with-azure-active-directory.md).

   If your deployment uses NavUserPassword authentication, you need the credentials (sign in email and password) of a user account later in this article.

- An Azure portal account

    You need an account for accessing the Azure portal. In most cases, this account is the same as your Business Central account. You use this account to access Microsoft Entra tenant via the Azure portal. The account must have application administrator permissions to create and manage app registrations.

## Register an application in Microsoft Entra ID

The first task is to use Azure portal to register an application for Business Central on your Microsoft Entra tenant. As part of the registration, you also give the relevant services access to the application. The purpose of registration is to ensure [!INCLUDE [prod_short](../developer/includes/prod_short.md)] on-premises and the services know each other's Microsoft Entra ID details.

> [!TIP]
> The following steps describe how to register a new application. However, if you're using Microsoft Entra authentication, you already have a registered application for [!INCLUDE [prod_short](../developer/includes/prod_short.md)]. So instead of registering a new application, you can use the existing application. But if you do, make sure you modify it based on the information in the steps that follow.

1. Sign in to the [Azure portal](https://portal.azure.com) and register an application for [!INCLUDE [prod_short](../developer/includes/prod_short.md)] on-premises in Microsoft Entra tenant.

    1. Follow the general guidelines at [Register your application with your Microsoft Entra tenant](/azure/active-directory/active-directory-app-registration).

        When you add an application to a Microsoft Entra tenant, you must specify the following information:

        |Setting|Description|
        |-------|-----------|
        |Name|Specify a name for your Business Central on-premises solution, such as *Business Central on-premises* or *Azure Services for Business Central on-premises*. |
        |Supported account types| Select **Accounts in any organizational directory (Any Microsoft Entra ID directory - Multitenant)**<br /><br />**Note:** [!INCLUDE [prod_short](../developer/includes/prod_short.md)] doesn't require the organization to be multitenant, not even if this field is set to multitenant. |
        |Redirect URI|Set the first box to **Web** to specify a web application. Enter the URL for your Business Central on-premises browser client, followed by *OAuthLanding.htm*, for example: `https://localhost/BC230/OAuthLanding.htm` `https://MyServer/BC230/OAuthLanding.htm` or `https://cronus.onmicrosoft.com/BC230/OAuthLanding.htm`. This file is used to manage the exchange of data between Business Central on-premises and other services through Microsoft Entra ID.<br> <br>**Important:** The URL must match the URL of Web client, as it appears in the browser address of the computer you're working on. For example, even though the actual URL might be `https://MyServer:443/BC230/OAuthLanding.htm`, the browser typically removes the port number `:443`.|

        When completed, an **Overview** displays in the portal for the new application.

    2. Copy the **Application (Client) ID** that was assigned the application and also redirect URL that you specified. You'll use this information later.

2. Create a client secret for the registered application.

    1. Follow the general guidelines at [Add credentials to your web application](/azure/active-directory/develop/quickstart-register-app#add-a-client-secret).

    2. Before you leave the **Certificates & secrets** page, copy the secret's value to a temporary location. The value isn't accessible once you leave the page. You'll use this key later in your client application code.

3. Grant the registered application delegated permission to access the required service APIs, like Power BI.

    From the registered application's overview page, select **API permissions** > **Add a permission**. Then, use the **Request API permissions** pane to locate the API and add permissions. For more information, see [Add permissions to access web APIs](/azure/active-directory/develop/quickstart-configure-app-access-web-apis#add-permissions-to-access-web-apis) in the Azure documentation.

    Use the following table to help you set the minimum permissions:

    |Feature|API | Permission name|Type|Description|
    |----|----|----------------|----|-----------|
    |All|Microsoft Graph | User.Read|Delegated|Sign in and read user profile|
    |[Business Central add-in for Excel](/dynamics365/business-central/admin-deploy-excel-addin)|[Business Central app registration name]|[Business Central app permission name]|Delegated|Allows users of the add-in for Excel to access the OData web services to read and write data.|
    |[Business Central Add-in for Outlook](Setting-up-Office-Add-Ins-Outlook-Inbox.md)|Microsoft Graph | EWS.AccessAsUser.All|Delegated|Gives the Business Central add-in for Outlook permission to mailbox data in Microsoft 365 (Exchange Online) or Exchange Server.|
    |[Exchange Contact Sync](/dynamics365/business-central/admin-synchronize-outlook-contacts)|Office 365 Exchange Online| Contacts.ReadWrite|Delegated|Allows the app to create, read, update, and delete user contacts.<br><br> **TIP** To find Office 365 Exchange Online, type it the search box on the **APIs my organization uses** tab.|
    ||| EWS.AccessAsUser.All|Delegated|Allows the app to have the same access to mailboxes as the signed-in user via Exchange Web Services.|
    |[OneDrive Integration](/dynamics365/business-central/admin-onedrive-integration)<sup>[\[1\]](#1)</sup>|SharePoint|AllSites.FullControl |Delegated|Have full control of all site collections|
    |||User.ReadWrite.All|Delegated|Read and write user profiles|
    |[Power BI Integration](/dynamics365/business-central/admin-powerbi-setup)|Power BI Service|Report.Read.All|Delegated|View all reports. Required for viewing Power BI reports in Business Central.|
    |||Workspace.Read.All|Delegated|View all workspaces. Required for viewing shared Power BI workspaces in Business Central.|
    |[Universal Print integration](/dynamics365/business-central/ui-specify-printer-selection-reports#set-up-universal-print)|Microsoft Graph |PrinterShare.ReadBasic.All|Delegated|Read basic information about printer shares. Required for using Universal Print printers.|
    |||PrintJob.Create|Delegated|Create print jobs. Required for using Universal Print printers|
    |||PrintJob.ReadBasic|Delegated|Read basic information of user's print jobs. Required for using Universal Print printers.|

    <sup>1</sup><a name="1"></a>For Business Central 2021 release wave 2 (version 19), the required permissions are different. Use these permissions instead: AllSites.Write, MyFiles.Write, User.Read.All.

4. Configure consent on each API permission according to your organizations policies.

   Consent is a process where users or admins authorize an application to access a resource, like a user's profile or mailbox, depending on the service. When a user attempts to sign in to the registered app for the first time, the app requests permission, and the user must accept to continue. As an admin, you can consent on behalf of all users, so they don't have to. To learn more, go to [More on API permissions and admin consent](/azure/active-directory/develop/quickstart-configure-app-access-web-apis#more-on-api-permissions-and-admin-consent) and [Introduction to permissions and consent](/azure/active-directory/develop/permissions-consent-overview).

5. If this is a new registered app, and not an update to an existing one, go to the next task to set it up in Business Central.

## Set up the registered application in Business Central

After you create the application registration, the next task is to configure the Business Central tenant to use it. You need the following information about the application registration: redirect URL, application (client) ID, and client secret.

> [!NOTE]
> Don't complete this task for configuring OneDrive integration with Business Central 2022 release wave 1 (version 20) and earlier. Instead, see [Configuring Business Central On-Premises for OneDrive](/dynamics365/business-central/admin-onedrive-integration-onpremises#set-up-the-connection-in--version-19-and-20) in the business functionality help.

1. In the top-right corner, choose the ![Tell me.](../developer/media/search-icon.png "Tell me what you want to do") icon, enter **Assisted Setup**, and then choose the related link.
2. Select **Set up your Microsoft Entra accounts**, then **Next**.

    The **Connect With Azure** page opens.
    <!--
    ![Setting the Microsoft Entra ID.](../developer/media/set-up-azure-ad.png)
    -->
3. In the **Redirect URL** field, make sure the URL matches the redirect URL that's assigned the registered Business Central application in Microsoft Entra ID.
4. In the **Application ID** field, specify the application (client) ID of the Business Central application in Microsoft Entra ID that you copied in the previous task.
5. In the **Key** field, specify the value of the client secret that's used by the Business Central application in Microsoft Entra ID.
6. Choose **Next**.

    If you're using NavUserPassword authentication, you're prompted to sign in to the Microsoft Entra tenant. In this case, enter the sign-in email and password of a valid account.

Unless you see an error message, you're now done. The [!INCLUDE [prod_short](../developer/includes/prod_short.md)] on-premises solution is registered and ready to connect to services such as Cortana Intelligence, or embedding Power BI in [!INCLUDE [prod_short](../developer/includes/prod_short.md)].

## Next step

The first time a feature that uses the registered application is accessed from [!INCLUDE [prod_short](../developer/includes/prod_short.md)], consent must be given to the Azure service. Consent can only be given by a Microsoft Entra admin user account. So, after you set up the registered the application in [!INCLUDE [prod_short](../developer/includes/prod_short.md)], make the initial connection to these services and give consent. As an example, see [Connect to Power BI from Business Central- one time only](/dynamics365/business-central/across-working-with-powerbi#connect-to-power-bi-from-business-central--one-time-only).

## Fixing problems

This section provides solutions to problems that might occur.

### Sorry, but we're having trouble signing you in

When you try to connect, you get a message similar to the following text:  

**AADSTS50011: The reply URL specified in the request does not match the reply URLs configured for the application: '1111111-aaaa-2222-bbbb-333333333333'**

To fix this issue, verify that the **Reply URL** in the Setup Microsoft Entra ID page is correct. It must match the Reply URL set on the registered app in Microsoft Entra ID.

### Couldn't connect to service

After authorizing the Azure service, you get a message similar to the following text:  

**We couldn't connect to [service name] using your Microsoft Entra application registration. Run the Set Up Microsoft Entra ID assisted setup again, and make sure all values are set correctly.**

This issue indicates there's a problem with the configuration of the Azure registered application used by the service. The problem is typically caused by incorrect values for either the **Redirect URL**, **Application ID**, or **Key** fields in the application registration. A common problem deals with the redirect URLs. Make sure the **Redirect URL** matches the redirect URL in the Azure portal and the URL of the Web client. To fix this issue, run the **Set Up Microsoft Entra ID** assisted setup and compare the values with the app registration in Azure.

## Problem consenting to the Microsoft Entra (Azure) services for initial connection

While consenting to the services for the initial connection, you keep getting prompted to consent instead of connecting, there may be a problem with the reply URL that used in the **Set up your Microsoft Entra accounts** assisted setup guide. The first part of the reply URL, before `OAuthLanding.htm`, should exactly match what appears in your browser URL when you open the Business Central web client. For example, if the browser URL is `https://localhost/BC230` on your computer, then the reply URL you provide must be `https://localhost/BC230/OAuthLanding.htm`. The reply URL must also be included in the app you registered in Microsoft Entra ID previously in this article. 
 
## See Also

[Business Central and Power BI](/dynamics365/business-central/admin-powerbi)  
[FAQ about Migrating to the Cloud from On-Premises Solutions](faq-migrate-data.md)  
[Deployment of [!INCLUDE[prod_long](../developer/includes/prod_long.md)]](../deployment/Deployment.md)  
[Migrating On-Premises Data to Business Central Online](migrate-data.md)  
