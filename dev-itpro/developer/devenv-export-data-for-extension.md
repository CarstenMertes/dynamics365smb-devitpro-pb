---
title: Adding data for Extensions
description: How you can add data such as permisisons, web services, and table data for an extension.
author: SusanneWindfeldPedersen
ms.date: 04/01/2021
ms.topic: how-to
ms.author: solsen
ms.reviewer: solsen
---

# Adding data for extensions

For your extension to run properly, configuration and starting data such as permission sets and table data may be needed. An extension can include the following types of data that can be imported for the tenant during the installation of the extension.

- Permission sets
- Web services
- Starting table data
- Custom report layouts

The data must be exported into files to be included in the extension. To use the export functions, you must use a container sandbox environment for [!INCLUDE [prod_short](includes/prod_short.md)]. Learn more in [Get started with the container sandbox development environment](devenv-get-started-container-sandbox.md).

## To add permission sets

1. Open the [!INCLUDE[bc_dev_shell](includes/bc_dev_shell.md)].
2. Export the relevant permission set using the `Export-NAVAppPermissionSet` cmdlet to export the permission set to a file. For example, the following command exports the BASIC permission set.

    `Export-NAVAppPermissionSet -ServerInstance DynamicsNAV160 -Path '.\PermissionSet.xml' -PermissionSetId BASIC`

    > [!NOTE]  
    > Export each permission set to a separate XML file.

3. Add the exported permission set files to the Visual Studio Code project that contains your extension.

    > [!WARNING]  
    > If you don't include a permission set with your extension, only users with the SUPER permission set will be able to use the extension.

    > [!IMPORTANT]  
    > With the latest version of [!INCLUDE [prod_short](includes/prod_short.md)] permissions are no longer defined as data in the application database. Permissions that can be created by using AL objects are called *system* permissions. Learn more in [Entitlements and permission sets overview](devenv-entitlements-and-permissionsets-overview.md).


## To add web services

1. Open the [!INCLUDE[bc_dev_shell](includes/bc_dev_shell.md)].
2. Export the relevant web service using the `Export-NAVAppTenantWebService` cmdlet to export the web service to a file. The following command exports the Customer Card page.

    `Export-NAVAppTenantWebService -ServerInstance DynamicsNAV160 -Path TenantWebService.xml -ServiceName Customer -ObjectType Page -ObjectId 21`

    > [!NOTE]  
    > Export each web service to a separate XML file.

3. Add the exported web services files to the Visual Studio Code project that contains your extension. An exported web service XML file looks like the following:

    ```XML
    <?xml version="1.0" encoding="utf-8"?>
    <ExportedData>
        <TenantWebServiceCollection>
            <TenantWebService>
                <ObjectType>Page</ObjectType>
                <ObjectID>21</ObjectID>
                <ServiceName>Customer</ServiceName>
                <Published>true</Published>
            </TenantWebService>
        </TenantWebServiceCollection>
    </ExportedData>
    ```
    
    You may also merge multiple XML files into one:
    ```XML
    <?xml version="1.0" encoding="utf-8"?>
    <ExportedData>
        <TenantWebServiceCollection>
            <TenantWebService>
                <ObjectType>Page</ObjectType>
                <ObjectID>21</ObjectID>
                <ServiceName>Customer</ServiceName>
                <Published>true</Published>
            </TenantWebService>
            <TenantWebService>
                <ObjectType>Page</ObjectType>
                <ObjectID>26</ObjectID>
                <ServiceName>Vendor</ServiceName>
                <Published>true</Published>
            </TenantWebService>
        </TenantWebServiceCollection>
    </ExportedData>
    ```

## To add table data 

1. Open the [!INCLUDE[bc_dev_shell](includes/bc_dev_shell.md)].
2. Export the relevant data using the `Export-NAVAppTableData` cmdlet to export the data to a file. This includes setting the path to a folder where you want the .navxdata file created. A data file in the format of `TAB<TABLEID>.navxdata` will be created. (Example: TAB10000.navxdata). 

    `Export-NAVAppTableData -ServerInstance DynamicsNAV160 -Path 'C:\NAVAppTableData' -TableId 10000`

    > [!NOTE]  
    > Export the data for each table to a separate XML file.

3. Add the exported table data files to the Visual Studio Code project that contains your extension.
4. Call the procedure in a Codeunit with the Subtype property `Install` or `Upgrade` and specify the table ID  in the `NavApp.LoadPackageData` procedure as shown in the following example.

    ```AL
    codeunit 50100 MyExtensionUpgrade
    {
        Subtype = Upgrade;
        trigger OnUpgradePerDatabase()
        begin
            NavApp.LoadPackageData(50100);
        end;
    }
    ```

    > [!WARNING]
    > An extension can only include table data for new tables that are added as part of the extension.

## To add custom report layouts

1. Open the [!INCLUDE[bc_dev_shell](includes/bc_dev_shell.md)].
2. Export the relevant report layouts using the `Export-NAVAppReportLayout` cmdlet to export to a file:

    `Export-NAVAppReportLayout -ServerInstance DynamicsNAV160 -Path .\ReportLayout.xml -LayoutId 1`

    > [!NOTE]  
    > Export each custom report layout to a separate XML file.

3. Add the exported custom report files to the Visual Studio Code project that contains your extension.

## Related information

[Developing extensions in AL](devenv-dev-overview.md)  
[Writing extension install code](devenv-extension-install-code.md)  
