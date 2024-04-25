---
title: FAQ about Migrating to Business Central Online
description: Get answers to your questions about migrating to the cloud from an on-premises solution.
author: jswymer

ms.reviewer: jswymer
ms.topic: conceptual
ms. search.keywords: cloud, edge
ms.date: 11/30/2022
ms.author: jswymer
---

# FAQ about migrating to Business Central online from on-premises solutions

[!INCLUDE[azure-ad-to-microsoft-entra-id](~/../shared-content/shared/azure-ad-to-microsoft-entra-id.md)]

This section contains answers to frequently asked questions about migrating from on-premises solutions to [!INCLUDE[prod_short](../developer/includes/prod_short.md)] online.  

> [!TIP]
> Check the tips in this article if your organization is not yet ready to migrate to [!INCLUDE [prod_short](../includes/prod_short.md)] online but are thinking hard about it. For more information about migration, see [Migrate On-Premises Data to Business Central Online](migrate-data.md).  

## Which products and versions are supported?

[!INCLUDE [bc-cloud-products](../includes/bc-cloud-products.md)]

For more information, see [Upgrading from Dynamics NAV to Business Central online](../administration/migrate-nav.md).

<!-- - Dynamics SL 2018 CU 1-->

### System requirements

To migrate to [!INCLUDE[prod_short](../developer/includes/prod_short.md)] online, the on-premises solution must use SQL Server 2016 or a later version, and the database must have compatibility level 130 or higher. The on-premises solution must also be one of the supported versions.  

For comparison, see the [System Requirements for [!INCLUDE[prod_long](../developer/includes/prod_long.md)] (on-premises) 2021 Release Wave 1](../deployment/system-requirements-business-central-v18.md) and subsequent versions.  

## How is my on-premises data migrated to my [!INCLUDE[prod_short](../developer/includes/prod_short.md)] online tenant?

Data is migrated using an Azure service called Azure Data Factory (ADF). ADF is a service that is always running within the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] online service manager. When you start the cloud migration, a data pipeline is created in the ADF service so that data can flow from your on-premises solution to your Business Central online tenant. If your data source is a local SQL Server instance, you're also asked to configure a self-hosted integration runtime (SHIR). The runtime is installed locally and manages the communication between the cloud services and your on-premises data without opening any ports or firewalls.  

## Are there any limits on the amount or type of data that can be migrated?

There are no restrictions on the type of data that can be migrated. [!INCLUDE [db-storage-limit](../includes/db-storage-limit.md)]  

We recommend that you reduce the number of companies that you're migrating data for in each migration run. You can specify which companies to include in the migration in the assisted setup wizard.  

If you want to add more companies after the first selection of companies, you can add more companies in the **Cloud Migration Management** page in Business Central online. For more information, see [Run the tool multiple times](migration-setup.md#rerunning-cloud-migration-setup-guide).

If you're looking at migrating databases larger than 80 GB, we recommend that you contact the support team and work with them to make sure that the migration is successful. If needed, you can also purchase more storage. For more information, go to [Managing Capacity](tenant-admin-center-capacity.md).  

## Is my SQL connection string required to set up the connection?

Yes. The SQL connection string is passed to Azure Data Factory, where it's encrypted and delivered to your Self-Hosted Integration Runtime. The connection string is used to communicate with your SQL Server instance during the data replication process. For more information, see [How do I find my SQL connection string?](#how-do-i-find-my-sql-connection-string).  

## How do I find my SQL connection string?

You can find the connection string in SQL Management Studio for an on-premise SQL Server database or in Azure portal for an Azure SQL database. The user name and password defined in the connection requires a SQL Authenticated user name/password

A connection string to an on-premise SQL Server database looks like this:

`Server={SQLServerName}{SQLServerInstance};Database={DatabaseName};User ID={UserName};Password={Password};`

A connection string to an Azure SQL database looks like this:

`Server=tcp:{ServerName},1433;Initial Catalog={DatabaseName};Persist Security Info=False; User ID={UserName};Password={Password};MultipleActiveResultSets=False;Encrypt=True;TrustServerCertificate=True;Connection Timeout=30;`

To learn more, go to [Define SQL database connection and integration runtime](migration-setup.md#define-sql-database-connection-and-integration-runtime).

## How do I find the Integration Runtime name or key?

Find the Integration Runtime name in the Microsoft Integration Runtime Manager, which you can find in your Windows system tray or by searching for the program. You must type the name. You can't copy and paste the name.  You can get the key from the **Cloud Migration Management** by selecting the **Get runtime service key** action. 

## I'm a hosting partner - do I need to configure the Self-Hosted Runtime Service for each tenant?

No, there's no limit on the number of tenants that can be added to your Self-Hosted Integration Runtime. Each added tenant has a dedicated pipeline created. However, if there are multiple tenants migrating using the same Integration Runtime, it's important to plan their migrations in a way that avoids overlapping in time. This will help prevent your Integration Runtime service from experiencing an excessive load.

## Will data from tables with code customizations migrate?

No, only tables that are available in both your on-premises solution and your [!INCLUDE[prod_short](../developer/includes/prod_short.md)] online tenant will migrate. Any customization must be made into an extension and installed on both your on-premises solution and your [!INCLUDE[prod_short](../developer/includes/prod_short.md)] online tenant to replicate.  

Yes, but it requires that someone defines tables mappings to move the customized fields. For more information, go to [Define Migration Table Mappings](migration-table-mapping.md). 

## Why are my permissions restricted in the Business Central online tenant?

When you connect your on-premises solution to [!INCLUDE [prod_short](../developer/includes/prod_short.md)] online as part of the migration, all existing users are automatically added to the *Intelligent Cloud* user group, unless they have the SUPER permission set. In this configuration, your on-premises solution is the primary source where all business transactions take place. The [!INCLUDE[prod_short](../developer/includes/prod_short.md)] online environment is read-only, and the data is used to generate intelligent business insights based on your on-premises data for you. We restrict permissions to prevent users from accidentally entering transactions or updating primary records only to have that information overwritten and lost when data replication takes place. Once the migration is complete, you can assign the relevant permissions to all users and stop using your on-premises solution.  

<!-- 
## Can I pause the migration?

You can switch off your connection to the [!INCLUDE [prod_short](../developer/includes/prod_short.md)] online environment at any point. At that point, your on-premises solution and [!INCLUDE[prod_short](../developer/includes/prod_short.md)] online become independent of one another.  

If you switch off the connection, and you want to use your [!INCLUDE[prod_short](../developer/includes/prod_short.md)] online environment as your primary solution to run and manage your business, you must reassign permissions to provide read/write access to the relevant users.  

For more information, see [Managing Users and Permissions](/dynamics365/business-central/ui-how-users-permissions).  -->

## Will my on-premises users and permissions replicate?

No. Since you aren't required to configure your on-premises solution with Microsoft Entra ID, we can't guarantee a mapping between on-premises users and users in your [!INCLUDE[prod_short](../developer/includes/prod_short.md)] online tenant. [!INCLUDE[prod_short](../developer/includes/prod_short.md)] online requires Microsoft Entra accounts, and users must be manually added. All permissions must be granted in the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] tenant, independent from your on-premises permissions.  

For more information, see [Managing Users and Permissions](/dynamics365/business-central/ui-how-users-permissions).

<!-- 
No. Because you aren't required to configure your on-premises solution with Microsoft Entra ID, we can't guarantee a mapping between on-premises users and users in your [!INCLUDE[prod_short](../developer/includes/prod_short.md)] online tenant. [!INCLUDE[prod_short](../developer/includes/prod_short.md)] online requires Microsoft Entra accounts, and users must be manually added. All permissions must be granted in the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] tenant, independent from your on-premises permissions. But cloud migration does provide a way for you to easily map on-premises users to online user accounts.

The following steps outline the general procedure:

1. For each on-premises user account, create a user account in your Microsoft Entra tenant and assign the user a Business Central license.

   1. Sign in to [Microsoft admin center](https://admin.microsoft.com).
   2. In **User Management**, select **Add User** and follow the instructions.

   For more information go to [Add users and assign licenses at the same time](/microsoft-365/admin/add-users/add-users?view=o365-worldwide).
2. Add the online user accounts to the Business Central online environment:

   1. Sign in to [Business Central online](https://businesscentral.dynamic.com).
   2. Open the **Users** page, select **Update users from Microsoft 365** and follow the instructions.
   3. Open the **Cloud Migration Management** page and select **Define User Mappings**.
   4. For each on-premises user, set the **Cloud User** field to the corresponding Microsoft Entra account.
   5. Select **OK** when done.  
3. Go to the **Users** page and grant the users permissions in Business Central.

   For more information, go to [Managing Users and Permissions](/dynamics365/business-central/ui-how-users-permissions).-->

<!--
## Can I view intelligent insights from cloud services in my on-premises solution?

No.  -->

## Is the data replication only one way?

Yes, data is only replicated from the on-premises solution to your Business Central online tenant for the purposes of migration. Once you start using [!INCLUDE [prod_short](../includes/prod_short.md)] online, you must stop using your on-premises solution.  

<!--
## Why did my Role Center change after the migration?

To keep the Role Center experience as clean as possible and avoid permission errors, we automatically hide actions that would generate a permission error for the user.  -->

## Should I uninstall all my Business Central extensions?

<!-- Not necessarily. Most extensions will run without issues in the online environment. You may want to consider uninstalling extensions that send data to an external service to avoid potential duplicated calls to that service. It's a best practice to test any extension in a sandbox tenant configured for the Business Central online environment that you're connecting to. --> 

No. But if your cloud migration includes data upgrade of a large amount of data, we recommend that you uninstall the extensions that that include any data to move. It speeds up the upgrade and overall cloud migration process. You can reinstall the extensions after the migration.


<!--## How do I build an extension that enables data replication?

The extension must be created in the same manner as any other extension. For data to replicate, you must add a **ReplicateData** property to your table and set the value to *True*. If your extension connects with an external service and you want to restrict any service calls from your [!INCLUDE[prod_short](../developer/includes/prod_short.md)] online tenant, a good practice would be to store the connection information in a separate table and set the **ReplicateData** property to *False*. This would enable you to keep the extension installed but prevent it from making any type of service calls from the read-only [!INCLUDE[prod_short](../developer/includes/prod_short.md)] tenant. Once the extension is installed in [!INCLUDE[prod_short](../developer/includes/prod_short.md)] online and on-premises, the data will begin to replicate.  -->

## See also

[Troubleshooting Cloud Migration](migration-troubleshooting.md)  
[Migrating On-Premises Data to Business Central Online](migrate-data.md)  
