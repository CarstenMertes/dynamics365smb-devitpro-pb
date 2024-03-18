---
title: "How to Unpublish and Uninstall an Extension"
description: "Description of the process of upublishing and uninstalling an extension"
author: jswymer
ms.custom: na
ms.date: 05/23/2022
ms.reviewer: na
ms.topic: conceptual
ms.author: jswymer
---

# Unpublishing and Uninstalling Extensions

Similar to how you make an extension available to tenant users, there's also three operations that are related to the removal of an extension: uninstalling, unpublishing, and synchronizing in clean mode. Each operation provides a different level of removal:

|Task|Description|
|---------|-----------|
|Uninstalling an extension|<ul><li>Done on the tenant level for a specific extension version.</li><li>Disables the extension on the tenant - making it unavailable to users in the client and removing any user interface that the extension provides.</li><li>Doesn't affect business data in the tenant, modify SQL, or run any user code. Data that has been collected by using the extension is preserved. As long as the extension hasn't been unpublished, it can be reinstalled and the data is still available.</li><li>For example, suppose you discovered an issue with the current extension. You could uninstall until a newer version is published.</li></ul> |
|Unpublishing an extension |<ul><li>Done on the [!INCLUDE[d365fin_server_md](includes/d365fin_server_md.md)] instance level for a specific extension version.</li><li> Deletes the extension package from the application database that is mounted on the server instance. The extension is no longer available for installation on tenants of the server instance.</li><li> Like uninstalling an extension, unpublishing doesn't affect business data in the tenant, modify SQL, or run any user code.</li><li>An extension **can't** be unpublished if it's installed on a tenant of the server instance.</li><li>For example, you would unpublish an extension version when it's no longer in use by any tenant. It prevents tenant users from using the extension again. You'd typically run this operation after an extension has been upgraded on all tenants from one extension version (for example, 11.0.0.1) to newer version (11.0.0.2). </li></ul>|
|Synchronizing in clean mode |<ul><li>Done on the tenant level for **all** versions of an extension.</li><li>Removes the database schema that's defined by the extension versions. This operation deletes all data in the extension. If a table or table extension was included in any version of the extension, the table or companion table will be deleted from the tenant database.</li><li>You can't synchronize in clean mode if any version of the extension is installed on a tenant of the server instance.</li><li>In production, use this mode primarily as a final cleanup step after all versions of an extension have been uninstalled and unpublished for good.</li><li> In development, this mode is useful to give you a "clean" environment when making database-schema related modifications.</li></ul>|

<!--
-   *Uninstalling* an extension is done on the tenant level for a specific extension version. Uninstalling an extension essentially disables the extension on the tenant - making it unavailable to users in the client and removing any user interface that the extension provides. Uninstalling an extension doesn't affect business data in the tenant, modify SQL, or run any user code. Data that has been collected through the use of the extension is preserved. So as long as the extension hasn't been unpublished, it can be reinstalled and the data is still available. Uninstalling an extension can be useful, for example, if you discovered an issue with current extension, and you do not want it available to users until a newer version is published.  

-   *Unpublishing* an extension is done on the [!INCLUDE[d365fin_server_md](includes/d365fin_server_md.md)] instance level for a specific extension version. This deletes the extension package from the application database that is mounted on the server instance. This means that the extension is no longer available for installation on tenants of the server instance. Like uninstalling an extension, this doesn't affect business data in the tenant, modify SQL, or run any user code. 

    An extension **can't** be unpublished if it's installed on a tenant of the server instance. You would unpublish an extension version when it's no longer in use by any tenant, and you want to prevent tenants from using it again. This is typically the case after an extension has been upgraded from one extension version (for example, 11.0.0.1) to newer version (11.0.0.2) on all tenants. 

-   *Synchonizing in clean mode* of an extension is done on the tenant level for all versions of an extension. It removes the database schema that is defined extension versions, which deletes all data in the extension. In other words, if a table or table extension was included in any version of the extension, then the respective full or companion table will be deleted from the tenant database, and data in the table is lost.

You can't synchronize in clean mode if any version of the extension is installed on a tenant of the server instance.
 
In production, this should primarily be done as a final cleanup step after all versions of an extension have been uninstalled and unpublished for good. During extension development, this can be useful in order to give the developer a "clean" environment when creating database schema related modifications (table extensions, tables). 
-->

## Uninstalling extensions

You can uninstall an extension by using the [!INCLUDE[adminshell](includes/adminshell.md)] or from the client. You can run the synchronizing in clean mode operation as part of the uninstall operation, instead of doing it after separately.

> [!IMPORTANT]
> - You can't uninistall an extension if any there are other installed extensions that are dependent on the extension. If you try, you'll get a message stating that there are dependent extensions and asking you to confirm whether you want to uninstall the extension and its dependents.
> - When you choose to run the synchronizing in clean mode operation when uninstalling, the database schema and data associated with dependent extensions will also be removed.

### Uninstall an extension by using [!INCLUDE[adminshell](includes/adminshell.md)] 

1. Start the [!INCLUDE[adminshell](includes/adminshell.md)]. 

    For more information, see [Business Central PowerShell Cmdlets](/powershell/business-central/overview).
2. To get a list of the extensions that are currently installed on a tenant, run the [Get-NAVAppInfo cmdlet](/powershell/module/microsoft.dynamics.nav.apps.management/get-navappinfo) with the `Tenant` parameter set.

    This cmdlet is useful when you uninstall the extension because you must provide information about the extension, like its name and version. 

    ```powershell
    Get-NAVAppInfo -ServerInstance YourDynamicsNAVServer -Tenant TenantID
    ```

    Replace `TenantID` with the tenant ID of the database. If you don't have a multitenant server instance, use `default` or omit this parameter. 

3. To uninstall an extension, run the [Uninstall-NAVApp cmdlet](/powershell/module/microsoft.dynamics.nav.apps.management/uninstall-navapp).

    The following example uninstalls an extension by using its extension package file path `.\MyExtension.app`. 

    ```powershell  
    Uninstall-NAVApp -ServerInstance YourDynamicsNAVServer -Path '.\MyExtension.app'  
    ``` 

    The following example uninstalls an extension by using its name `My Extension` and version (in this case `1.0.0.0`):

    ```powershell  
    Uninstall-NAVApp -ServerInstance YourDynamicsNAVServer -Name "My Extension" -Version 1.0.0.0
    ```  

    The following example combines the Get-NAVAppInfo and Uninstall-NAVApp cmdlets into a single command:

    ```powershell  
    Get-NAVAppInfo -ServerInstance YourDynamicsNAVServer -Name 'My Extension' -Version 1.0.0.0 | Uninstall-NAVApp
    ```  

    If you want to run synchronizing in clean mode operation, include the `-ClearSchema` parameter.

### Uninstall an extension by using the client  

1. In [!INCLUDE[d365fin_long_md](includes/d365fin_long_md.md)], use search to open the **Extension Management** page.

    In the **Extension Management** window, you can view the extensions that are installed on the tenant 
2. Choose an extension, and choose the **Uninstall** action.

3. If you want to delete data in tables owned by the extension, turn on the **Delete Extension Data** switch. This action does the same as the `-ClearSchema` parameter with the Uninstall-NavApp cmldet. This action can't be undone.

For more information, see [Uninstall an Extension](/dynamics365/business-central/ui-extensions-install-uninstall#uninstall-an-extension) in the business functionality help.

### Delete orphaned extension data

If you want to keep the data for an uninstalled app, you can delete the data later by using the **Delete Orphaned Extension Data** page. The **Delete Orphaned Extension Data** page lists the apps that you still have data for. To delete the data, choose the app, and then choose **Delete Data**. 

There are several reasons for why you should delete orphaned extension data. First, it frees up database capacity. Second, it reduces the row size in the companion table used to store data for extension tables. This will, in turn, speed up data operations on that table.

## Unpublish extensions

You unpublish an extension on a [!INCLUDE[d365fin_server_md](includes/d365fin_server_md.md)] instance by using the [!INCLUDE[adminshell](includes/adminshell.md)].

1. Start the [!INCLUDE[adminshell](includes/adminshell.md)]. 

    For more information, see [Business Central PowerShell Cmdlets](/powershell/business-central/overview).

2. To get a list of the extensions that are currently published on a tenant, run the [Get-NAVAppInfo cmdlet](/powershell/module/microsoft.dynamics.nav.apps.management/get-navappinfo) without the `Tenant` parameter.

    This is useful because a server instance can have several published extensions. Unpublishing an extension requires that you provide specific information about the extension, like the name or version. 

    ```powershell
    Get-NAVAppInfo -ServerInstance YourDynamicsNAVServer
    ```

3. To unpublish the extension, run the [Unpublish-NAVApp cmdlet](/powershell/module/microsoft.dynamics.nav.apps.management/unpublish-navapp). You can unpublish the extension by specifying the path to extension package file or the extension name and version.

    The following example unpublishes an extension by using its extension package file path `.\MyExtension.app`. 

    ```powershell  
    Unpublish-NAVApp -ServerInstance YourDynamicsNAVServer -Path '.\MyExtension.app'  
    ``` 
    
    The following example unpublishes an extension by using its name `My Extension` and version (in this case `1.0.0.0`):

    ```powershell  
    Unpublish-NAVApp -ServerInstance YourDynamicsNAVServer -Name "My Extension" -Version 1.0.0.0
    ```  

    The following example combines the Get-NAVAppInfo and Unpublish-NAVApp cmdlets into a single command:

    ```powershell  
    Get-NAVAppInfo -ServerInstance YourDynamicsNAVServer -Name 'My Extension' -Version 1.0.0.0 | Unpublish-NAVApp
    ```

### Unpublish an extension by using the client  

1. In [!INCLUDE[d365fin_long_md](includes/d365fin_long_md.md)], use search to open the **Extension Management** page.

    In the **Extension Management** window, you can view the extensions that are installed on the tenant. 
2. Choose an extension where **Published As** is *not set to* **Global**, and choose the **Unpublish** action.

## Synchronizing (clean mode) an extension after uninstallation

1. Start the [!INCLUDE[adminshell](includes/adminshell.md)]. 

    For more information, see [Business Central PowerShell Cmdlets](/powershell/business-central/overview).
2.Run the [Sync-NAVAPP](/powershell/module/microsoft.dynamics.nav.apps.management/sync-navapp) cmdlet with the `-Mode`parameter set to `Clean`.

    ```powershell
    Sync-NAVApp -ServerInstance YourDynamicsNAVServer -Tenant 'TenantID' -Name 'My Extension' -Mode Clean
    ```

## See Also

[Publishing and Installing an Extension](devenv-how-publish-and-install-an-extension-v2.md)  
[Developing Extensions](devenv-dev-overview.md)  
[Analyzing Extension Lifecycle Telemetry](../administration/telemetry-extension-lifecycle-trace.md)  
