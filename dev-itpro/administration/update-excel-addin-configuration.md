---
title: "Update the Excel add-in configuration"
description: Learn about how to change the Excel add-in setup so that it works with the update in July 2022.
author: jswymer
ms.author: jswymer
ms.custom: na
ms.topic: conceptual
ms.date: 12/29/2023
---
# Modify the Excel add-in configuration to support July 2022 update

[!INCLUDE[azure-ad-to-microsoft-entra-id](~/../shared-content/shared/azure-ad-to-microsoft-entra-id.md)]

Starting in July 2022, Microsoft rolls out an update to the Excel add-in. The update helps to secure the connection between the add-in and [!INCLUDE [prod_short](../developer/includes/prod_short.md)]. The update requires that you modify your organization's Microsoft Entra ID configuration so that users can continue using the add-in.

> [!NOTE]
> You can make the changes that are described in this article at any time. The existing Excel add-in will work with the changes. So we recommend that you make the changes as soon as possible to avoid any down time when the update occurs.

## How the update affects your organization

The update affects organizations that have configured the Excel add-in to work with [!INCLUDE [prod_short](../developer/includes/prod_short.md)] on premises or similar deployment variants, such as hosted or private cloud. [!INCLUDE [prod_short](../developer/includes/prod_short.md)] online customers aren't affected.

After Microsoft updates the Excel add-in, users will no longer be able to sign in to the add-in. The sign-in process appears to halt without completing. Users experience this problem when using the Edit in Excel feature in the Business Central, or working with new and existing Excel files that utilize the add-in. The inability to connect Excel to Business Central applies to all Excel clients and Excel versions supported by the add-in, and all Business Central versions.

## What you need to do to prepare

You'll have to change to the existing Microsoft Entra app registration that's set up for the add-in to use the new single-page application (*spa*) redirect URI instead of the legacy *web* redirect URI. The change requires you have administrative permissions. It only has to be done once for the whole organization. Your registered app might already be configured for *spa*. You can also use the following steps to verify.

1. Sign in to [Azure portal](https://portal.azure.com).
2. Select **Microsoft Entra ID**. 
3. Under **Manage**, select **App Registrations**.
4. Select the app that was registered to enable users to sign in to the Excel add-in. 
5. Under **Manage**, select **Manifest**.
6. In the manifest, find the following `"url"`entry and change `"type": "Web"` to `"type": "Spa"`:

    ```json  
    {
        "url": "https://az689774.vo.msecnd.net/dynamicsofficeapp/v1.3.0.0/*",
        "type": "Spa"
    }
    ```

> [!IMPORTANT]
> Your experience may vary if your Microsoft Entra app registration also includes redirect URIs for other services. Don't not change other redirect URIs for other services or for the [!INCLUDE [prod_short](../developer/includes/prod_short.md)] Web client as part of this change. To check if other services are affected by similar security hardening exercises and require re-configuration, contact the service provider.

## See also

[Setting up the Business Central Add-in for Excel in [!INCLUDE[prod_short](../developer/includes/prod_short.md)] on-premises](configuring-excel-addin.md)  
[Registering an application Microsoft Entra ID](/azure/active-directory/develop/quickstart-register-app)    
