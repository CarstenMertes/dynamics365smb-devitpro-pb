---
title: "Business Central Administration Shell"
description: Read about the PowerShell cmdlets managing Business Central Server instances and extensions for on-premises deployments.
author: jswymer
ms.custom: bap-template
ms.reviewer: jswymer
ms.topic: conceptual
ms.author: jswymer
ms.date: 04/15/2025
ms.service: dynamics-365-op
---

# Business Central Administration Shell

The [!INCLUDE[adminshell](../developer/includes/adminshell.md)] includes PowerShell cmdlets for administering Business Central on-premises deployments. You use it for configuring Business Central Server and Web server instances, databases, users, and more. You also use it to manage extensions, like publishing, syncing, installing and upgrading.

## Install the Business Central Administration Shell

The [!INCLUDE[adminshell](../developer/includes/adminshell.md)] is installed together with [!INCLUDE[server](../developer/includes/server.md)] components by using the Business Central Setup wizard. To install it, run the setup.exe that's available on the installation media (DVD). Follow the wizard, and choose either the **Install Demo** option or the **Server** option in the customized setup. For more information, see [Install Using Setup](../deployment/install-using-setup.md).

## Run the Business Central Administration Shell

To run the shell, you have to be a member of the local administrator group on the computer. There are a couple ways to run the shell.

- One way is from the **Start** menu or **Search** on your desktop. Select **Start** or **Search**, type *[!INCLUDE[adminshell](../developer/includes/adminshell.md)]*, right-click it, then select **Run as administrator**.

- Another way is from Windows PowerShell. Start Windows PowerShell as an administrator. At the prompt, run the following command:

    ```powershell
    Import-Module -Name C:\Program Files\Microsoft Dynamics 365 Business Central\nnn\Service\navadmintool.ps1
    ```

    Replace `C:\Program Files\Microsoft Dynamics 365 Business Central\nnn` with the path to your server installation.

## Get help on the cmdlets

To view the available cmdlets, enter the following command at the prompt:

```powershell  
Get-Command *NAV*  
```

To get help with syntax, options, and examples for a specific cmdlet in Business Central version 23 or earlier, enter the following command:

```PowerShell  
Get-Help <cmd name> -full
```  

For example, to get Help about the **Get-NAVServerInstance** cmdlet, type the following command.  

```powershell   
Get-Help Get-NAVServerInstance -full
```  

Help with syntax, options, and examples isn't available starting with version 24. Use the online version of the help on Microsoft Learn.  

To open the online help, enter the following command:  

```powershell
Get-Help <cmd name> -online  
```  

### Learn more

For more information about [!INCLUDE[adminshell](../developer/includes/adminshell.md)] cmdlets, see [Administration Cmdlets ](/powershell/module/microsoft.dynamics.nav.management).  

For more information about Windows PowerShell, see [Windows PowerShell Getting Started Guide](https://go.microsoft.com/fwlink/?LinkID=252252).  

## Related information

[Configuring Business Central Server Instances](configure-server-instance.md)  
[Configuring Business Central Web Server Instances](configure-web-server.md)  
[Publish and Install Extenstions](../developer/devenv-how-publish-and-install-an-extension-v2.md)  
