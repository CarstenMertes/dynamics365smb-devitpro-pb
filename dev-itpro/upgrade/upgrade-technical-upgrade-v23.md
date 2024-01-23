---
title: "Technical Upgrade to Version 23"
description: Describes how to do a technical upgrade from Business Central V19, V20, V21, V22 to V23
ms.custom: bap-template
ms.date: 08/14/2023
ms.reviewer: jswymer
ms.topic: conceptual
ms.author: jswymer
author: jswymer
---
# Technical upgrade to version 23

Use this process to upgrade any of the following versions to the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2023 Release Wave 2 platform (version 23). This process won't upgrade the application to the latest version.

- [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2023 release wave 1 (version 22)
- [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2022 release wave 2 (version 21)
- [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2022 release wave 1 (version 20)

[![Upgrade on customized Business Central application.](../developer/media/23-technical-upgrade.png)](../developer/media/23-technical-upgrade.png#lightbox)

## Before you begin

Review the information in this section before you start upgrading your deployment.

[!INCLUDE[include-tech-upgrade-note.md](../developer/includes/include-tech-upgrade-note.md)]

### Single-tenant and multitenant deployments

[!INCLUDE[upgrade_single_vs_multitenant](../developer/includes/upgrade_single_vs_multitenant.md)]

### Prepare new runtime packages

[!INCLUDE[upgrade_runtime_packages](../developer/includes/upgrade_runtime_packages.md)]

### PowerShell variables used in tasks

Many of the steps in this article use PowerShell cmdlets, which require that you provide values for various parameters. To make it easier for copying or scripting in PowerShell, the steps use the following variables for parameter values. Replace the text between the `" "` with the correct values for your environment. 

```powershell
$OldBcServerInstance = "The name of the Business Central server instance for your previous version, for example: BC220"
$NewBcServerInstance = "The name of the Business Central server instance for version 23, for example: BC230"
$TenantId = "The ID of the tenant to be upgraded. If not using a multitenant server instance, set the variable to default, or omit -Tenant parameter."
$TenantDatabase = "The name of the Business Central tenant database to be upgraded, for example: Demo Database BC (22-0)" 
$ApplicationDatabase = "The name of the Business Central application database in a multitenant environment, for example: My BC App DB. For a single-tenant deployment, this is the same as $TenantDatabase." 
$DatabaseServer = "The SQL Server instance that hosts the databases. The value has the format server_name\instance_name, For example: localhost\BCDEMO"
$PartnerLicense = "The file path and name of the partner license"
$AddinsFolder = 'The file path to the Add-ins folder of version 23 server installation, for example, C:\Program Files\Microsoft Dynamics 365 Business Central\230\Service\Add-ins'
$CustomerLicense = "The file path and name of the customer license"
```

## Task 1: Install version 23

1. Choose a version 23 that's compatible with your current platform version.

    There are several updates for each Business Central version. The update of your current version must be compatible version 23 update that you want to upgrade to. For more information, see [[!INCLUDE[prod_long](../developer/includes/prod_long.md)] Upgrade Compatibility Matrix](upgrade-v14-v15-compatibility.md). If your solution, for example, is currently running 20.6, you can't upgrade to 21.0. You'll have to wait until 21.1 is available. 

2. Before you install version 23, it can be useful to create desktop shortcuts to the version 16.0 tools, such as the [!INCLUDE[adminshell](../developer/includes/adminshell.md)], and [!INCLUDE[devshell](../developer/includes/devshell.md)] because the Start menu items for these tools will be replaced with the version 23.0 tools.

3. Install version 23 components.

    You'll keep previous version installed for now. When you install version 23, you must either specify different port numbers for components (like the [!INCLUDE[server](../developer/includes/server.md)] instance and web services) or stop the version 18.0 [!INCLUDE[server](../developer/includes/server.md)] instance before you run the installation. Otherwise, you'll get an error that the [!INCLUDE[server](../developer/includes/server.md)] failed to install.

    For more information, see [Installing Business Central Using Setup](../deployment/install-using-setup.md).

4. Copy the contents of the **NavEwsWrapper**, and the entire **Timeline** and **PingPong** add-in folders from the version 20 server instance installation to the same folder the new version 23 server instance. For the **Timeline** and **PingPong**, you'll have to add the folders because they're not included in the version 23 server add-ins folder. Replace existing files when prompted.

   By default, the **Add-ins** folder path is C:\Program Files\Microsoft Dynamics 365 Business Central\<server instance>\Service\Add-ins. You'll have to stop the v21 server instance to copy the files.

    > [!IMPORTANT]
    > This step is important, otherwise you won't be about to recompile the Business Central system application and base application. If you don't repair these extension, you'll get errors when you try to install them or mount the tenant.

## Task 2: Upgrade permission sets

Version 18 introduced the capability to define permissions sets as AL objects, instead of as data. Permissions sets as AL objects is now the default and recommended model for defining permissions. However, for now, you can choose to use the legacy model, where permissions are defined and stored as data in the database. Whichever model you choose, there are permission set-related tasks you'll have to go through before and during upgrade.

For more information, see [Upgrading Permissions Sets and Permissions](upgrade-permissions.md).

<!-- ## Task 3: Modify base app to support custom reports

> [!NOTE]
> This task is only required when upgrading from version 17, 18, or 19. 

Version 20 introduced new platform-rendering of reports. To support this change, you'll have to modify the base application code to ensure that custom layouts run correctly after upgrade.

Version 20 introduces platform-rendering of reports. If you're solution includes custom report layouts, you may have to modify the base application so that the layouts run correctly after upgrade. Whether you need to complete this task will depend on the customizations.

For more information, see [Upgrading Reports](upgrade-reports.md#).-->

## <a name="Preparedb"></a> Task 3: Prepare databases

In this task, you prepare the application and tenant databases for the upgrade.

1. Make backup of the database.

2. Disable data encryption.

    If the current server instance uses data encryption, disable it. You can enable it again after upgrading.

    For more information, see [Managing Encryption and Encryption Keys](how-to-export-and-import-encryption-keys.md#encryption).

    Instead of disabling encryption, you can export the current encryption key, which you'll then import after upgrade. However, we recommend disabling encryption before upgrading.

3. (Single-tenant only) Uninstall all extensions from the old tenants.

    Run the [!INCLUDE[adminshell](../developer/includes/adminshell.md)] for the previous version, like 18, as an administrator. [!INCLUDE[open-admin-shell](../developer/includes/open-admin-shell.md)]

    Use the [Uninstall-NAVApp](/powershell/module/microsoft.dynamics.nav.apps.management/uninstall-navapp) cmdlet to uninstall an extension. For example, together with the Get-NAVAppInfo cmdlet, you can uninstall all extensions with a single command:

    ```powershell 
    Get-NAVAppInfo -ServerInstance $OldBcServerInstance  | % { Uninstall-NAVApp -ServerInstance $OldBcServerInstance -Name $_.Name -Version $_.Version }
    ```

4. Unpublish all system, test, and application symbols.

    To unpublish symbols, use the Unpublish-NAVAPP cmdlet. You can unpublish all symbols by using the Get-NAVAppInfo cmdlet with the `-SymbolsOnly` switch as follows:

    ```powershell 
    Get-NAVAppInfo -ServerInstance $OldBcServerInstance  -SymbolsOnly | % { Unpublish-NAVApp -ServerInstance $OldBcServerInstance -Name $_.Name -Version $_.Version }
    ```

    [What are symbols?](upgrade-overview-v15.md#Symbols)  

5. (Multitenant only) Dismount the tenants from the application server instance.

    To dismount a tenant, use the [Dismount-NAVTenant](/powershell/module/microsoft.dynamics.nav.management/dismount-navtenant) cmdlet:

    ```powershell
    Dismount-NAVTenant -ServerInstance $OldBcServerInstance -Tenant $TenantId
    ```

6. Stop the server instance.

    ```powershell
    Stop-NAVServerInstance -ServerInstance $OldBcServerInstance
    ```
7. [!INCLUDE[flf-license](../developer/includes/flf-license.md)] 

## Task 4: Convert application database to version 23

This task runs a technical upgrade on the application database. A technical upgrade converts the current database to the version 23.0 platform. This conversion updates the system tables of the database to the new schema (data structure). It also provides the latest platform features and performance enhancements.

> [!IMPORTANT]
> The conversion does not modify the application objects, but it will remove any modifications that you have made to system tables. After the conversion you will no longer be able to use it with current version.

1. Start [!INCLUDE[adminshell](../developer/includes/adminshell.md)] for version 23.0 as an administrator.

   [!INCLUDE[open-admin-shell](../developer/includes/open-admin-shell.md)]

2. Run the [Invoke-NAVApplicationDatabaseConversion cmdlet](/powershell/module/microsoft.dynamics.nav.management/invoke-navapplicationdatabaseconversion) to start the conversion. In a multitenant deployment, run this cmdlet against the application database.

    ```powershell
    Invoke-NAVApplicationDatabaseConversion -DatabaseServer $DatabaseServer -DatabaseName $ApplicationDatabase
    ```

    When completed, a message like the following displays in the console:

    ```powershell
    DatabaseServer      : .\BCDEMO
    DatabaseName        : Demo Database BC (20-0)
    DatabaseCredentials :
    DatabaseLocation    :
    Collation           :
    ```

[!INCLUDE[convert_azure_sql_db_timeout](../developer/includes/convert_azure_sql_db_timeout.md)]

## Task 5: Configure version 23 server

When you installed version 23 in **Task 1**, a version 23 [!INCLUDE[server](../developer/includes/server.md)] instance was created. In this task, you change server configuration settings that are required to complete the upgrade. Some of the changes are only required for the upgrade and can be reverted after you complete the upgrade.

1. Set the server instance to connect to the application database.

    ```powershell
    Set-NAVServerConfiguration -ServerInstance $NewBcServerInstance -KeyName DatabaseName -KeyValue $ApplicationDatabase
    ```

    In a single tenant deployment, this command mounts the tenant automatically. For more information, see [Connecting a Server Instance to a Database](../administration/connect-server-to-database.md).

2. If you want to use permission sets defined as data, set the `UserPermissionSetsFromExtensions` setting to `false`.

    ```powershell
    Set-NavServerConfiguration -ServerInstance $NewBcServerInstance -KeyName "UsePermissionSetsFromExtensions" -KeyValue false
    ```

3. Disable task scheduler on the server instance for purposes of upgrade.

    ```powershell
    Set-NavServerConfiguration -ServerInstance $NewBcServerInstance -KeyName "EnableTaskScheduler" -KeyValue false
    ```

    Be sure to re-enable task scheduler after upgrade if needed.
4. Restart the server instance.

    ```powershell
    Restart-NAVServerInstance -ServerInstance $NewBcServerInstance
    ```

## <a name="UploadLicense"></a> Task 6: Import [!INCLUDE[prod_short](../developer/includes/prod_short.md)] partner license  

If you've gotten a new [!INCLUDE[prod_short](../developer/includes/prod_short.md)] partner license, make sure that it has been uploaded to the database. To upload the license, use the [Import-NAVServerLicense cmdlet](/powershell/module/microsoft.dynamics.nav.management/import-navserverlicense):

```powershell
Import-NAVServerLicense -ServerInstance $NewBcServerInstance -LicenseFile $PartnerLicense
```

For more information, see [Uploading a License File for a Specific Database](../cside/cside-upload-license-file.md#UploadtoDatabase).  

## Task 7: Recompile published extensions

Compile all published extensions against the new platform.

[!INCLUDE[repair_runtime_packages](../developer/includes/repair_runtime_packages.md)]

1. To compile an extension, use the [Repair-NAVApp](/powershell/module/microsoft.dynamics.nav.apps.management/repair-navapp) cmdlet, For example:

    ```powershell  
    Repair-NAVApp -ServerInstance $NewBcServerInstance -Name $ExtName -Version $ExtVersion
    ```

    To compile all published extensions at once, you can use this command:

    ```powershell  
    Get-NAVAppInfo -ServerInstance $NewBcServerInstance | Repair-NAVApp  
    ```

2. If errors occur for any of the extensions, especially the system application or base application, you'll have to fix them before proceeding.

    For more information, see [Fixing compilation errors for technical upgrade](technical-upgrade-fix-compilation-errors.md).

    In some cases, fixing these errors will require that you create new versions of the extensions, which you'll have to publish and upgrade.

3. Restart the server instance.

    ```powershell
    Restart-NAVServerInstance -ServerInstance $NewBcServerInstance
    ```

## Task 8: Synchronize tenant

1. (Multitenant only) Mount the tenant to the new Business Central Server instance.

    You'll have to do this step and the next for each tenant. For more information, see [Mount or Dismount a Tenant](../administration/mount-dismount-tenant.md).

    To mount the tenant, use the [Mount-NAVTenant](/powershell/module/microsoft.dynamics.nav.management/mount-navtenant) cmdlet:

    ```powershell
    Mount-NAVTenant -ServerInstance $NewBcServerInstance -DatabaseName $TenantDatabase -DatabaseServer $DatabaseServer -Tenant $TenantId -AllowAppDatabaseWrite
    ```

    > [!IMPORTANT]
    > You must use the same tenant ID for the tenant that was used in the old deployment; otherwise you'll get an error when mounting or syncing the tenant. If you want to use a different ID for the tenant, you can either use the `-AlternateId` parameter now or after upgrading, dismount the tenant, then mount it again using the new ID and the `OverwriteTenantIdInDatabase` parameter.  
    >  
    > For upgrade, set the `-AllowAppDatabaseWrite` parameter. After upgrade, you can dismount and mount the tenant again without the parameter if needed.

2. Synchronize the tenant.
  
    Use the [Sync-NAVTenant](/powershell/module/microsoft.dynamics.nav.management/sync-navtenant) cmdlet:

    ```powershell  
    Sync-NAVTenant -ServerInstance $NewBcServerInstance -Tenant $TenantId -Mode Sync
    ```

    For a single-tenant deployment, you can either set the `$TenantId` to `default` or omit the `-Tenant $TenantId` parameter. For more information about syncing, see [Synchronizing the Tenant Database and Application Database](../administration/synchronize-tenant-database-and-application-database.md).

3. If you published new extension versions, for example, in task 7 to fix compilation errors for system application and base application, synchronize the new versions with the tenant. Synchronize the extensions in order of dependency. The general order is:

    1. System Application
    2. Base Application
    3. Microsoft extensions
    4. Custom extensions

    For example:

    ```powershell  
    Sync-NAVApp -ServerInstance $NewBcServerInstance -Name "System Application" -Version "<version>" -Tenant $TenantId
    ```

    ```powershell  
    Sync-NAVApp -ServerInstance $NewBcServerInstance -Name "Base Application" -Version "<version>" -Tenant $TenantId
    ```

## Task 9: Upgrade extensions

> [!NOTE]
> This task is only required if you've published new versions fo extensions, for example, as part of task 7. In this case, you'll run a data upgrade on the new versions.

It's important to consider the extension dependency graph when upgrading. The general order is:

1. System Application
2. Base Application
3. Microsoft extensions
4. Custom extensions

To run the data upgrade on an extension, use the [Start-NAVAppDataUpgrade cmdlet](/powershell/module/microsoft.dynamics.nav.apps.management/start-navappdataupgrade) cmdlet:

```powershell
Start-NAVAppDataUpgrade -ServerInstance $NewBcServerInstance -Name "<extension name>" -Tenant $TenantId -Version <new version>
```

At this point, your solution has been updated to the latest platform.

## Task 10: Reinstall extensions (single-tenant only)

In this task, you reinstall the same extensions that were installed on the tenant before, except for any extensions that you upgraded in the previous task. Reinstalling extensions is only required on single tenant environments.

It's important to consider the extension dependency graph when installing them. The general order is:

1. System Application
2. Base Application
3. Microsoft extensions
4. Custom extensions

To install an extension, you use the [Install-NAVApp cmdlet](/powershell/module/microsoft.dynamics.nav.apps.management/install-navapp):

```powershell
Install-NAVApp -ServerInstance $NewBcServerInstance -Name <extension name>" -Tenant $TenantId -Version $OldVersion
```

At this point, your solution has been updated to the latest platform.

## Task 11: <a name="JSaddins"></a>Upgrade control add-ins

[!INCLUDE[upgrade-control-addins](../developer/includes/upgrade-control-addins.md)]

## Task 12: Install upgraded permissions sets

In this task, you install the custom permission sets that you upgraded earlier in this procedure. The steps depend on whether you've decided to use permission sets as AL objects or as data.

### For permission sets as AL objects

1. Publish the extension or extensions that include the permission sets.
2. Sync the extensions with the tenant.
3. Install the extensions on the tenant.

### For permission sets as data in XML

1. Set the `UserPermissionSetsFromExtensions` setting of the [!INCLUDE[server](../developer/includes/server.md)] instance to `false`.

    ```powershell
    Set-NavServerConfiguration -ServerInstance $NewBcServerInstance -KeyName "UsePermissionSetsFromExtensions" -KeyValue false
    ```

2. Restart the serve instance.
3. Open the [!INCLUDE[webclient](../developer/includes/webclient.md)].
4. Search for and open the **Permission Sets** page.
5. Select **Import Permission Sets**, and follow the instructions to import the XML file.

For more information, see [To export and import a permission set](/dynamics365/business-central/ui-define-granular-permissions#to-export-and-import-a-permission-set).

## Post-upgrade tasks

1. [!INCLUDE[delegation-upgrade](../developer/includes/delegation-upgrade.md)]
2. Enable task scheduler on the server instance.
3. (Multitenant only) For tenants other than the tenant that you use for administration purposes, if you mounted the tenants using the `-AllowAppDatabaseWrite` parameter, dismount the tenants, then mount them again without using the `-AllowAppDatabaseWrite` parameter.
4. If you want to use data encryption as before, enable it.

   For more information, see [Managing Encryption and Encryption Keys](how-to-export-and-import-encryption-keys.md#encryption).

   Optionally, if you exported the encryption key instead of disabling encryption earlier, import the encryption key file to enable encryption.
5. Import the customer license.

    Import the customer license by using the [Import-NAVServerLicense cmdlet](/powershell/module/microsoft.dynamics.nav.management/import-navserverlicense), as you did with the partner license. You'll have to restart the server instance afterwards.

    ```powershell
    Import-NAVServerLicense -ServerInstance $NewBcServerInstance -LicenseFile $CustomerLicense
    Restart-NAVServerInstance -ServerInstance $NewBcServerInstance
    ```

## See Also

[Upgrading to Business Central](upgrading-to-business-central.md)  
[Business Central Compatibility matrix](upgrade-v14-v15-compatibility.md)
