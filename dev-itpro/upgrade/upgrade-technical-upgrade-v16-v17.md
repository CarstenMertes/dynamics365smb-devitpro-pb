---
title: "Technical Upgrade from Version 16 to Version 17"
description: Describes how to do a technical upgrade from Business Central 16 to 17
ms.custom: na
ms.date: 04/01/2021
ms.reviewer: na
ms.topic: conceptual
ms.author: jswymer
author: jswymer
---
# Technical Upgrade from Version 16 to Version 17

Use this process to upgrade from [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2020 release wave 1 (version 16) to the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2020 release wave 2 platform (version 17). This process won't upgrade the application to the latest version.

 ![Upgrade on customized Business Central application.](../developer/media/bc16-to-17-technical-upgrade-unmodified-app.png "Upgrade on customize Business Central application")   

#### Single-tenant and multitenant deployments

[!INCLUDE[upgrade_single_vs_multitenant](../developer/includes/upgrade_single_vs_multitenant.md)]

## Prerequisites

1. Your version 16 platform is compatible with version 17.

    There are several updates for version 16. The updates have a compatible version 17 update. For more information, see [[!INCLUDE[prod_long](../developer/includes/prod_long.md)] Upgrade Compatibility Matrix](upgrade-v14-v15-compatibility.md). For example, if your solution is currently running 16.6, you can't upgrade to 17.0. You must wait until 17.1 is available.  

2. Disable data encryption.

    If the current server instance uses data encryption, disable it. You can enable it again after upgrading.

    For more information, see [Managing Encryption and Encryption Keys](how-to-export-and-import-encryption-keys.md#encryption).

    Instead of disabling encryption, you can export the current encryption key, which you'll then import after upgrade. However, we recommend disabling encryption before upgrading.

<!--
## Task 2: Rewrite code for obsoleted system tables

In version 16, a number of tables have been deprecated and replaced by new tables. You must rewrite code that uses the deprecated tables to use the new tables. For a list of the deprecated tables and new tables, see [Deprecated Tables](deprecated-tables.md).

<!--
This change introduces several breaking changes. For more information about resolving the changes, see [Breaking Changes](https://github.com/microsoft/ALAppExtensions/blob/master/BREAKINGCHANGES.md). To complete this task, you modify your base application AL source, and compile a new extension.
-->
## <a name="Preparedb"></a> Task 1: Prepare databases

In this task, you prepare the application and tenant databases for the upgrade.

1. Make backup of the database.

<!--
2. Make sure that you have the extension packages for all published extensions.

    You'll need these packages later to re-publish and install the extensions again.
-->

2. (Single-tenant only) Uninstall all extensions from the old tenants.

    Run the [!INCLUDE[adminshell](../developer/includes/adminshell.md)] for version 16.0 as an administrator. [!INCLUDE[open-admin-shell](../developer/includes/open-admin-shell.md)]
    
    Use the [Uninstall-NAVApp](/powershell/module/microsoft.dynamics.nav.apps.management/uninstall-navapp) cmdlet to uninstall an extension. For example, together with the Get-NAVAppInfo cmdlet, you can uninstall all extensions with a single command:

    ```powershell 
    Get-NAVAppInfo -ServerInstance <BC16 server instance> | % { Uninstall-NAVApp -ServerInstance <BC16 server instance> -Name $_.Name -Version $_.Version }
    ```

3. Unpublish all system, test, and application symbols.

    To unpublish symbols, use the Unpublish-NAVAPP cmdlet.  You can unpublish all symbols by using the Get-NAVAppInfo cmdlet with the `-SymbolsOnly` switch as follows:

    ```powershell 
    Get-NAVAppInfo -ServerInstance <BC16 server instance> -SymbolsOnly | % { Unpublish-NAVApp -ServerInstance <BC16 server instance> -Name $_.Name -Version $_.Version }
    ```

    [What are symbols?](upgrade-overview-v15.md#Symbols)  

4. (Multitenant only) Dismount the tenants from the application server instance.

    To dismount a tenant, use the [Dismount-NAVTenant](/powershell/module/microsoft.dynamics.nav.management/dismount-navtenant) cmdlet:

    ```powershell
    Dismount-NAVTenant -ServerInstance <BC16 server instance> -Tenant <tenant ID>
    ```

5. Stop the server instance.

    ```powershell
    Stop-NAVServerInstance -ServerInstance <BC16 server instance>
    ```

## Task 2: Install version 17

1. Before you install version 17, it can be useful to create desktop shortcuts to the version 16.0 tools, such as the [!INCLUDE[admintool](../developer/includes/admintool.md)], [!INCLUDE[adminshell](../developer/includes/adminshell.md)], and [!INCLUDE[devshell](../developer/includes/devshell.md)] because the Start menu items for these tools will be replaced with the version 17.0 tools.

2. Install version 17 components.

    You'll keep version 16 installed for now. When you install version 17, you must either specify different port numbers for components (like the [!INCLUDE[server](../developer/includes/server.md)] instance and web services) or stop the version 16.0 [!INCLUDE[server](../developer/includes/server.md)] instance before you run the installation. Otherwise, you'll get an error that the [!INCLUDE[server](../developer/includes/server.md)] failed to install.

    For more information, see [Installing Business Central Using Setup](../deployment/install-using-setup.md).

## Task 3: Copy Dynamics Online Connect add-in

The Dynamics Online Connect add-in has been deprecated in version 17. As a result, it has been removed from the DVD and is no longer installed as part of the [!INCLUDE[server](../developer/includes/server.md)]. However, when doing a technical upgrade, it is still required for the old System Application. To meet this requirement, copy the **Add-ins\Connect** folder of the version 16 server installation to the **Add-ins** folder of the version 17 server installation.

## Task 4: Convert the version 16.0 application database

This task runs a technical upgrade on the application database. A technical upgrade converts the database from the version 16.0 platform to the version 17.0 platform. This conversion updates the system tables of the database to the new schema (data structure). It also provides the latest platform features and performance enhancements.

> [!IMPORTANT]
> The conversion does not modify the application objects, but it will remove any modifications that you have made to system tables. After the conversion you will no longer be able to use it with Business Central 14.

1. Start [!INCLUDE[adminshell](../developer/includes/adminshell.md)] for version 17.0 as an administrator.

   [!INCLUDE[open-admin-shell](../developer/includes/open-admin-shell.md)]

2. Run the [Invoke-NAVApplicationDatabaseConversion cmdlet](/powershell/module/microsoft.dynamics.nav.management/invoke-navapplicationdatabaseconversion) to start the conversion. In a multitenant deployment, run this cmdlet against the application database.

    ```powershell
    Invoke-NAVApplicationDatabaseConversion -DatabaseServer <database server>\<database instance> -DatabaseName "<BC16 database name>"
    ```

    When completed, a message like the following displays in the console:

    ```powershell
    DatabaseServer      : .\BCDEMO
    DatabaseName        : Demo Database BC (16-0)
    DatabaseCredentials :
    DatabaseLocation    :
    Collation           :
    ```
[!INCLUDE[convert_azure_sql_db_timeout](../developer/includes/convert_azure_sql_db_timeout.md)]

## Task 5: Configure version 17 server

When you installed version 17 in **Task 1**, a version 17 [!INCLUDE[server](../developer/includes/server.md)] instance was created. In this task, you change server configuration settings that are required to complete the upgrade. Some of the changes are only required for version 16 to version 17.0 upgrade and can be reverted after you complete the upgrade.

1. Set the server instance to connect to the application database.

    ```powershell
    Set-NAVServerConfiguration -ServerInstance <BC17 server instance> -KeyName DatabaseName -KeyValue "<BC17 database name>"
    ```

    In a single tenant deployment, this command mounts the tenant automatically. For more information, see [Connecting a Server Instance to a Database](../administration/connect-server-to-database.md).

2. Disable task scheduler on the server instance for purposes of upgrade.

    ```powershell
    Set-NavServerConfiguration -ServerInstance <BC17 server instance> -KeyName "EnableTaskScheduler" -KeyValue false
    ```

    Be sure to re-enable task scheduler after upgrade if needed.
3. Restart the server instance.

    ```powershell
    Restart-NAVServerInstance -ServerInstance <BC17 server instance>
    ```

## <a name="UploadLicense"></a> Task 6: Upload [!INCLUDE[prod_short](../developer/includes/prod_short.md)] partner license  

If you have a new [!INCLUDE[prod_short](../developer/includes/prod_short.md)] partner license, make sure that it has been uploaded to the database. To upload the license, use the [Import-NAVServerLicense cmdlet](/powershell/module/microsoft.dynamics.nav.management/import-navserverlicense): 

```powershell
Import-NAVServerLicense -ServerInstance <BC17 server instance> -LicenseFile "<path to the license>"
```

For more information, see [Uploading a License File for a Specific Database](../cside/cside-upload-license-file.md#UploadtoDatabase).  

## Task 7: Publish new system symbols

Use the Publish-NAVApp cmdlet to publish the new symbols extension package. This package is called **System.app**. If you've installed the **AL Development Environment**, you find the file in the installation folder. By default, the folder path is C:\Program Files (x86)\Microsoft Dynamics 365 Business Central\170\AL Development Environment.

```powershell
Publish-NAVApp -ServerInstance <BC17 server instance> -Path "<path to the System.app file>" -PackageType SymbolsOnly
```

## Task 8: Recompile published extensions

Compile all published extensions against the new platform.

1. To compile an extension, use the [Repair-NAVApp](/powershell/module/microsoft.dynamics.nav.apps.management/repair-navapp) cmdlet, For example:

    ```powershell  
    Repair-NAVApp -ServerInstance <server instance> -Name <extension name> -Version <extension name>
    ```

    To compile all published extensions at once, you can use this command:

    ```powershell  
    Get-NAVAppInfo -ServerInstance <server instance> | Repair-NAVApp  
    ```

2. Restart the server instance.

    ```powershell
    Restart-NAVServerInstance -ServerInstance <server instance>
    ```

## Task 9: Synchronize tenant

1. (Multitenant only) Mount the tenant to the new Business Central Server instance.

    You'll have to do this step and the next for each tenant. For more information, see [Mount or Dismount a Tenant](../administration/mount-dismount-tenant.md).
 
2. Synchronize the tenant.
  
    Use the [Sync-NAVTenant](/powershell/module/microsoft.dynamics.nav.management/sync-navtenant) cmdlet:

    ```powershell  
    Sync-NAVTenant -ServerInstance <server instance> -Tenant <tenant ID> -Mode Sync
    ```

    For a single-tenant deployment, you can either set the `<tenant ID>` to `default` or omit the `-Tenant <tenant ID>` parameter. For more information about syncing, see [Synchronizing the Tenant Database and Application Database](../administration/synchronize-tenant-database-and-application-database.md).

## Task 10: Reinstall extensions

Skip this task for a multitenant environment. In this task, you reinstall the same extensions that were installed on the tenant before.

To install an extension, you use the [Install-NAVApp cmdlet](/powershell/module/microsoft.dynamics.nav.apps.management/install-navapp).

1. If your solution uses the System Application, install this first.

    ```powershell 
    Install-NAVApp -ServerInstance <server instance> -Name "System Application" -Version <extension version>
    ```

    Replace `<extension version>` with the exact version of the published System Application.

2. Install the Base Application.

    ```powershell
    Install-NAVApp -ServerInstance <server instance> -Name "Base Application" -Version <extension version>
    ```

    Replace `<extension version>` with the exact version of the published System Application.

3. Install the Application extension.

    ```powershell
    Install-NAVApp -ServerInstance <server instance> -Name "Application" -Version <extension version>
    ```

    Replace `<extension version>` with the exact version of the published Application extension.

    For more information about the Application extension, see [The Microsoft_Application.app File](../developer/devenv-application-app-file.md).
4. Install other extensions, including Microsoft and third-party extensions.

    ```powershell
    Install-NAVApp -ServerInstance <server instance name> -Name <extension name> -Version <extension version>
    ```

At this point, your solution has been updated to the latest platform.
<!--
PS C:\Windows\system32> Install-NAVApp -ServerInstance $NewInstanceName -Name "Intelligent Cloud Base"
WARNING: This license is not compatible with this version of Business Central.
WARNING: This license is not compatible with this version of Business Central.
WARNING: UnhandledErrorMessage
Install-NAVApp : The socket connection was aborted. This could be caused by an error processing your message or a receive timeout being exceeded by the remote host, or an underlying network resource issue. Local socket timeout was '10675199.02:48:05.4775807'.
At line:1 char:1
+ Install-NAVApp -ServerInstance $NewInstanceName -Name "Intelligent Cl ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [Install-NAVApp], CommunicationException
    + FullyQualifiedErrorId : System.ServiceModel.CommunicationException,Microsoft.Dynamics.Nav.Apps.Management.Cmdlets.InstallNavApp
-->

## Task 11: <a name="JSaddins"></a>Upgrade control add-ins

The [!INCLUDE[server](../developer/includes/server.md)] installation includes new versions of the Microsoft-provided Javascript-based control add-ins, like Microsoft.Dynamics.Nav.Client.BusinessChart, Microsoft.Dynamics.Nav.Client.VideoPlayer, and more. If your solution uses any of these control add-ins, upgrade them to the latest version.

To upgrade the control add-ins, do the following steps:

1. Open the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] client.
2. Search for and open the **Control Add-ins** page.
3. Choose **Actions** > **Control Add-in Resource** > **Import**.
4. Locate and select the .zip file for the control add-in and choose **Open**.

    The .zip files are located in the **Add-ins** folder of the [!INCLUDE[server](../developer/includes/server.md)] installation. There's a subfolder for each add-in. For example, the path to the Business Chart control add-in is `C:\Program Files\Microsoft Dynamics 365 Business Central\170\Service\Add-ins\BusinessChart\Microsoft.Dynamics.Nav.Client.BusinessChart.zip`.
5. After you've imported all the new control add-in versions, restart Business Central Server instance.

Alternatively, you can use the [Set-NAVAddin cmdlet](/powershell/module/microsoft.dynamics.nav.management/set-navaddin) of the [!INCLUDE[adminshell](../developer/includes/adminshell.md)]. For example, the following commands update the control add-ins installed by default. Modify the commands to suit:

```powershell
$InstanceName = 'BC170'
$ServicesAddinsFolder = 'C:\Program Files\Microsoft Dynamics 365 Business Central\170\Service\Add-ins'
Set-NAVAddIn -ServerInstance $InstanceName -AddinName 'Microsoft.Dynamics.Nav.Client.BusinessChart' -PublicKeyToken 31bf3856ad364e35 -ResourceFile ($AppName = Join-Path $ServicesAddinsFolder 'BusinessChart\Microsoft.Dynamics.Nav.Client.BusinessChart.zip')
Set-NAVAddIn -ServerInstance $InstanceName -AddinName 'Microsoft.Dynamics.Nav.Client.FlowIntegration' -PublicKeyToken 31bf3856ad364e35 -ResourceFile ($AppName = Join-Path $ServicesAddinsFolder 'FlowIntegration\Microsoft.Dynamics.Nav.Client.FlowIntegration.zip')
Set-NAVAddIn -ServerInstance $InstanceName -AddinName 'Microsoft.Dynamics.Nav.Client.OAuthIntegration' -PublicKeyToken 31bf3856ad364e35 -ResourceFile ($AppName = Join-Path $ServicesAddinsFolder 'OAuthIntegration\Microsoft.Dynamics.Nav.Client.OAuthIntegration.zip')
Set-NAVAddIn -ServerInstance $InstanceName -AddinName 'Microsoft.Dynamics.Nav.Client.PageReady' -PublicKeyToken 31bf3856ad364e35 -ResourceFile ($AppName = Join-Path $ServicesAddinsFolder 'PageReady\Microsoft.Dynamics.Nav.Client.PageReady.zip')
Set-NAVAddIn -ServerInstance $InstanceName -AddinName 'Microsoft.Dynamics.Nav.Client.PowerBIManagement' -PublicKeyToken 31bf3856ad364e35 -ResourceFile ($AppName = Join-Path $ServicesAddinsFolder 'PowerBIManagement\Microsoft.Dynamics.Nav.Client.PowerBIManagement.zip')
Set-NAVAddIn -ServerInstance $InstanceName -AddinName 'Microsoft.Dynamics.Nav.Client.RoleCenterSelector' -PublicKeyToken 31bf3856ad364e35 -ResourceFile ($AppName = Join-Path $ServicesAddinsFolder 'RoleCenterSelector\Microsoft.Dynamics.Nav.Client.RoleCenterSelector.zip')
Set-NAVAddIn -ServerInstance $InstanceName -AddinName 'Microsoft.Dynamics.Nav.Client.SatisfactionSurvey' -PublicKeyToken 31bf3856ad364e35 -ResourceFile ($AppName = Join-Path $ServicesAddinsFolder 'SatisfactionSurvey\Microsoft.Dynamics.Nav.Client.SatisfactionSurvey.zip')
Set-NAVAddIn -ServerInstance $InstanceName -AddinName 'Microsoft.Dynamics.Nav.Client.SocialListening' -PublicKeyToken 31bf3856ad364e35 -ResourceFile ($AppName = Join-Path $ServicesAddinsFolder 'SocialListening\Microsoft.Dynamics.Nav.Client.SocialListening.zip')
Set-NAVAddIn -ServerInstance $InstanceName -AddinName 'Microsoft.Dynamics.Nav.Client.VideoPlayer' -PublicKeyToken 31bf3856ad364e35 -ResourceFile ($AppName = Join-Path $ServicesAddinsFolder 'VideoPlayer\Microsoft.Dynamics.Nav.Client.VideoPlayer.zip')
Set-NAVAddIn -ServerInstance $InstanceName -AddinName 'Microsoft.Dynamics.Nav.Client.WebPageViewer' -PublicKeyToken 31bf3856ad364e35 -ResourceFile ($AppName = Join-Path $ServicesAddinsFolder 'WebPageViewer\Microsoft.Dynamics.Nav.Client.WebPageViewer.zip')
Set-NAVAddIn -ServerInstance $InstanceName -AddinName 'Microsoft.Dynamics.Nav.Client.WelcomeWizard' -PublicKeyToken 31bf3856ad364e35 -ResourceFile ($AppName = Join-Path $ServicesAddinsFolder 'WelcomeWizard\Microsoft.Dynamics.Nav.Client.WelcomeWizard.zip')
```

## Task 12: Post-upgrade

1. Enable task scheduler on the server instance.
2. (Multitenant only) For tenants other than the tenant that you use for administration purposes, if you mounted the tenants using the `-AllowAppDatabaseWrite` parameter, dismount the tenants, then mount them again without using the `-AllowAppDatabaseWrite` parameter.
3. If you want to use data encryption as before, enable it.

   For more information, see [Managing Encryption and Encryption Keys](how-to-export-and-import-encryption-keys.md#encryption).

   Optionally, if you exported the encryption key instead of disabling encryption earlier, import the encryption key file to enable encryption.

## See Also

[Upgrading to Business Central](upgrading-to-business-central.md)  
[Business Central Compatibility matrix](upgrade-v14-v15-compatibility.md)
