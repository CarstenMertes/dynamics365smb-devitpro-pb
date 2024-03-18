---
title: Setting up App Key Vaults for Business Central
description: Describes how to use an Azure Key vault with Business Central extensions for online.
ms.custom: na
ms.date: 04/08/2022
ms.reviewer: na
ms.topic: conceptual
author: jswymer
---
# Setting up App Key Vaults for [!INCLUDE[prod_short](../developer/includes/prod_short.md)] Online

[!INCLUDE[2020_releasewave2](../includes/2020_releasewave2.md)]

[!INCLUDE[azure-ad-to-microsoft-entra-id](~/../shared-content/shared/azure-ad-to-microsoft-entra-id.md)]

AppSource apps for [!INCLUDE[prod_short](../developer/includes/prod_short.md)] can be developed to get secrets from Azure Keys Vaults. The app key vault feature is readily available for use on the service by all App Source apps. However, there are some onboarding tasks required.

> [!IMPORTANT]
> With [!INCLUDE [prod_short](../developer/includes/prod_short.md)] online, App key vaults can only be used with AppSource apps. They're not supported with per-tenant extensions.

> [!TIP]
> You must also specify secrets in a key vault if you deploy [!INCLUDE [prod_short](../developer/includes/prod_short.md)] as part of the Embed App program. Especially if you must support the Outlook add-in, in which case you must specify secrets for TEMPORARYDOCUMENTSTORAGEACCOUNT and TEMPORARYDOCUMENTSTORAGEKEY. <!--For more information, see [Setting Up the Office Add-Ins for Outlook Integration with [!INCLUDE[prod_short](../developer/includes/prod_short.md)]](Setting-up-Office-Add-Ins-Outlook-Inbox.md).-->

For more information about developing extensions with key vaults, see [Using Key Vault Secrets in [!INCLUDE[prod_short](../developer/includes/prod_short.md)] Extensions](../developer/devenv-app-key-vault.md).

## Create the Azure Key Vault with secrets

In this task, you create a key vault in Azure, and add the secrets that you want to make available to your extensions. An extension can use up to two key vaults, so you can create more than one.

There are different ways to create an Azure key vault. For example, you can use the Azure portal, Azure CLI, and more.

The easiest way is to use the Azure portal. For instructions, see [Quickstart: Set and retrieve a secret from Azure Key Vault using the Azure portal](/azure/key-vault/secrets/quick-create-portal). 

For using other methods, see [Azure Key Vault Developer's Guide](/azure/key-vault/general/developers-guide#creating-and-managing-key-vaults).

## Provision the key reader application in your Microsoft Entra tenant

Your Business Central online solution is configured to use a Microsoft Entra application for reading key vault secrets. The application is called **Dynamics 365 Business Central ISV Key Vault Reader**. Microsoft manages the key vault reader application, however, there are a couple tasks that you have to do to enable it. First, the application must be provisioned on your Microsoft Entra tenant, as described here.

To provision the key vault reader application, use the [Microsoft Entra ID PowerShell module](/powershell/module/azuread).

1. Open Windows PowerShell as an administrator.
2. Install the Microsoft Entra ID PowerShell module.

    ```powershell
    Install-Module AzureAD 
    ```
3. Import the Microsoft Entra ID module.

    ```powershell
    Import-Module AzureAD 
    ```
4. Connect to your [!INCLUDE[prod_short](../developer/includes/prod_short.md)] Microsoft Entra tenant.

    1. Run the following command:

       ```powershell
       Connect-AzureAD 
       ```
    2. Provide your sign-in name and password when prompted.

4. Create a Microsoft Entra service principal using the following command:
      
    ```powershell
    New-AzureADServicePrincipal -AppId 7e97dcfb-bcdd-426e-8f0a-96439602627a
    ```
    
    `7e97dcfb-bcdd-426e-8f0a-96439602627a` is the Application (client) ID of Microsoft's centralized Microsoft Entra application.
    
    This step provisions the application in your Microsoft Entra tenant, where it now "lives" together with your key vaults.

## Grant the key vault reader application permission to your key vaults

The next task is to grant the key vault reader application permission to read secrets from your key vaults. The steps in this task are done from the [Azure portal](https://portal.azure.com).

1. Open the key vault in the portal.
2. Select **Access policies**, then **Add Access Policy**.
3. Set **Secret Permissions** to **Get**.
4. Choose **Select principal**, and on the right, search for either the application (client) ID **7e97dcfb-bcdd-426e-8f0a-96439602627a** or the display name **Dynamics 365 Business Central ISV Key Vault Reader**. 
5. Select **Add**, then **Save**.

## Contact Microsoft to enable the App Key Vault feature

Send an email to [bcappkeyvaultonboard@microsoft.com](mailto:bcappkeyvaultonboard@microsoft.com) to start the onboarding process following this guideline:

- If it is a new AppSource app, you should send the email after you have published the app on Partner Center. When the app has been onboarded to the app key vault, you then need to publish a new version of the app to Partner Center.

- If it is an existing AppSource app, you can send the email at any time, but it will only take effect when you publish a new version of the app to Partner Center.

<!-- Do this step before you publish your updated extension to Partner Center.-->

The onboarding process involves a manual verification step that verifies that you own the Microsoft Entra tenant that contains the key vaults.

Provide the following information in the email:

- Your Microsoft Entra tenant ID. Obtain this information from the Azure portal by going to the Microsoft Entra ID Overview page.
- Your AppSource extensions, including names and App IDs, that should be enabled to read secrets from your key vaults. **Note: It is important that all your AppSource extensions that need access to a key vault are included, as it is not enough to just set the key vault property in your `app.json` manifest files.**
- Confirmation that the app is already published on AppSource.
- Optionally, a screenshot from the Azure portal showing the key vault and its access policies. The screenshot can help Microsoft catch configuration mistakes early in the process.


## See Also  

[Security Considerations With App Key Vaults](../developer/devenv-app-key-vault.md#security)  
[Monitoring and Troubleshooting App Key Vaults](../developer/devenv-app-key-vault.md#troubleshooting)  
[Configuring Business Central Server](configure-server-instance.md)  