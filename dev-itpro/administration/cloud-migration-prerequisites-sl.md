---
title: Cloud Migration Prerequisites for Dynamics SL
description: Learn about the requirements for cloud migration in Dynamics SL on-premises and online.
author: lcontreras 
ms.author: jswymer
ms.reviewer: jswymer
ms.topic: conceptual
ms.date: 12/13/2024
ms.custom: bap-template
---

# Cloud migration prerequisites for Dynamics SL

This article outlines requirements on the [!INCLUDE [dyn_gp_prod](../includes/dyn_gp_prod.md)] on-premises and online environments for cloud migration. Review this information before you start the cloud migration.

## Destination online environment

- Customer has a [!INCLUDE [prod_short](../includes/prod_short.md)] online tenant  

- At least one user has *SUPER* permissions in the target company in [!INCLUDE [prod_short](../includes/prod_short.md)] online.

  Users assigned with *SUPER* permissions are the only users who can make changes in [!INCLUDE[prod_short](../developer/includes/prod_short.md)] online target company. Users who don't have *SUPER* permissions are automatically reassigned to the intelligent cloud user group, which limits them to read-only access to data. For more information, go to [Working with environments during cloud migration](migrate-business-central-on-premises.md#working-with-environments-during-cloud-migration).

  If you're the person who sets up and runs the cloud migration, you must have *SUPER* permissions and admin role in Microsoft admin center. If you're running cloud migration as a delegated admin, a Business Central user with *SUPER* permissions has to grant you permission. The permission is granted when you try to run the **Cloud Migration Setup**. For more information, go to [About delegated administrators](migration-setup-sl.md#about-delegated-administrators).

- Install the Business Central migration apps

  In the [!INCLUDE [prodadmincenter](../developer/includes/prodadmincenter.md)], open the environment that you intend to migrate your data to, and then choose the **Apps** action. Make sure that these apps have the latest updates installed:

  - Intelligent Cloud Base  
  - [!INCLUDE [dyn_sl_prod](../includes/dyn_sl_prod.md)] Intelligent Cloud 
  - [!INCLUDE [dyn_sl_prod](../includes/dyn_sl_prod.md)] Intelligent Cloud US (for US clients only)
  - [!INCLUDE [dyn_sl_prod](../includes/dyn_sl_prod.md)] History SmartLists  

  > [!IMPORTANT]
  > Migrating from [!INCLUDE [dyn_gp_prod](../includes/dyn_sl_prod.md)] using the **Cloud Migration Setup** assisted setup guide is currently only supported for the following markets:  
  >
  > - United States
  > - Canada
  > - United Kingdom
  > - Australia

## Source on-premises environment

- [!INCLUDE [dyn_sl_prod](../includes/dyn_sl_prod.md)] 2015 or later

  If the solution is based on an older version of the on-premises product, upgrade to the latest supported version.

- Database

  <!--The database can be hosted on SQL Server or Azure SQL Database.-->  

  The database can be hosted on SQL Server. The SQL Server database must meet the following requirements:
  - Uses SQL Server 2016 SP1 or later.
  - Compatibility level set to 130 or higher.
  - TCP/IP is enabled. For more information, go to [Enable or Disable a Server Network Protocol](/sql/database-engine/configure-windows/enable-or-disable-a-server-network-protocol) in the SQL Server documentation. 
  - Configured for SQL Server authentication.

    > [!IMPORTANT]
    > The sign in account used for SQL server authentication must have the **sysadmin** role on the server level and **db_owner** role on the database level.

### Is a data upgrade needed?

A cloud migration can be performed either on a live system or from a backup. 
 
- For a migration from a live system, the database is running a production workload and must therefore use a nondeveloper SKU of SQL Server. So if you're running your [!INCLUDE [dyn_sl_prod](../includes/dyn_sl_prod.md)] production environment on a SQL Server version 2014 or earlier, you need to upgrade the database before starting your cloud migration project. You might want to consider using an Azure SQL Managed Instance resource as a stepping stone. This type of Azure SQL database allows for importing a database backup and also supports most of the on-premises features of SQL Server.

- For a migration from a backup, you can just restore the backup using a SQL Server 2022 (or later) developer edition and run the migration project from there, as long as you don't use that SQL Server for other workloads.

## Other

- Self-hosted integration runtime machine (local on-premises database only; not Azure Database Server)

   The computer from which to run the cloud migration and self-hosted integration runtime should meet the requirements described in [Create and configure a self-hosted integration runtime](/azure/data-factory/create-self-hosted-integration-runtime?tabs=data-factory#prerequisites).

## Next steps

- [Migrate Dynamics SL Data to the Cloud](migrate-dynamics-SL.md)  
