---
title: Prepare and plan for cloud migration from Business Central on-premises
description: This article provides recommendations to help you define your cloud migration strategy and get environments and users ready for cloud migration.
author: jswymer
ms.author: jswymer
ms.reviewer: jswymer
ms.topic: conceptual
ms.date: 01/23/2024
ms.custom: bap-template 
---
# Prepare and plan for cloud migration from Business Central on-premises

This article provides recommendations to help you define your cloud migration strategy and get environments and users ready for cloud migration.

## Determine what data to migrate

The data that's migrated is determined on two levels: per-company and per-extension.

### Company data

When a company is migrated, data in company-specific tables of base application is migrated, along with company-specific data belonging to other extensions (for information, see the next section).

You can choose to migrate data for all companies or only specific companies. It's recommended to determine which companies to migrate upfront to save time and resources. Keep in mind that the more companies you replicate in a single operation, the longer the migration takes. The cloud migration capabilities are optimized to migrate data in batches of up to 10 companies. If you have more than 250 companies, it's recommended to plan to run the migration in smaller batches. For more information, see [Optimizing cloud migration performance](migration-optimize-replication.md#reduce-the-number-of-companies-migrated).

[!INCLUDE [migrate-limits](../developer/includes/migrate-limits.md)]

> [!NOTE]
> Per-database tables are always migrated, no matter which companies are selected for a migration run.

### Extension data

In general, on-premises data in table objects and table extension objects belonging to an extension is only migrated if the following conditions are met:

- The extension is installed on online environment.
- The extension's [ReplicateData property](../developer/properties/devenv-replicatedata-property.md) is set to `true`.

Because `true` is the default setting, most extensions that are installed on the [!INCLUDE[prod_short](../includes/prod_short.md)] online environment will have table data migrated.  

In certain circumstances, you might not want to migrate all data. Here are a couple examples:

- The extension is installed in the [!INCLUDE[prod_short](../includes/prod_short.md)] online environment but not in the [!INCLUDE [prod_short](../includes/prod_short.md)] on-premises solution

    In this case, [!INCLUDE[prod_short](../includes/prod_short.md)] attempts to migrate the data but shows a warning. Because the extension isn't installed on-premises, any table related to that extension table isn't migrated, and warning notifications appear in the cloud migration status page.

    If you own the extension, we recommend you set the **ReplicateData** property to *No* on the extension tables. If you don't, and if you want data to migrate, install the extension in both [!INCLUDE[prod_short](../includes/prod_short.md)] online and your on-premises solution. If you don't want data to migrate, uninstall the extension from the [!INCLUDE[prod_short](../includes/prod_short.md)] online environment.  

- The extension references a base table

    This condition can cause your base table to appear empty when you view data in your [!INCLUDE[prod_short](../includes/prod_short.md)] online tenant. In such cases, uninstall the extension from your [!INCLUDE[prod_short](../includes/prod_short.md)] online tenant and then run the cloud migration process again.

    Business Central inserts the default values and records into the table extensions automatically. If there are any problems, you can use the **Repair Companion Table Records** action on the **Cloud Migration Management** page to insert the missing table extension record

> [!TIP]
> Use the **Cloud Migration Management** page to verify that data migrated correctly. [!INCLUDE [bc-cloud-migrate-tableext](../includes/bc-cloud-migrate-tableext.md)]

For more information, see [FAQ about migrating to Business Central online from on-premises solutions](faq-migrate-data.md) and [Troubleshooting cloud migration](migration-troubleshooting.md).  

## Estimate the data size in your [!INCLUDE[prod_short](../includes/prod_short.md)] online tenant

In the online version of [!INCLUDE[prod_short](../developer/includes/prod_short.md)], data is compressed using the SQL Server data compression feature. This condition means that the data size in your on-premises database might not match the data size when migrated to the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] service. For more information on estimating the compressed size of your data, see [Estimating the data size in your Business Central online tenant](./cloud-migration-estimate-compressed-data-size.md). 

## Plan advanced migration approach

It's important to have a solid migration strategy in place to ensure a smooth transition. Most migrations can run from the on-premises production database with minimal downtime for end users. However, for especially large migrations, it might be better to run migration from a backup of the on-premises database deployed as Azure SQL Database. Doing migrations this way improves migration speeds and minimizes performance loss and downtime on the on-premises production database.

1. [Enable change tracking](/sql/relational-databases/track-changes/enable-and-disable-change-tracking-sql-server) on the on-premises production database for the expected number of days between the first backup for replication and the next time you'll back up and replicate. A minimum of three days is enforced. The number of days for which change tracking is enabled can't be changed later without resetting change tracking altogether.


   > [!NOTE]
   > - Long retention periods for change tracking data might cause database resource starvation when high volumes of data are changed on the database, which may lead to reduced database performance and/or loss of the change tracking data. Pick a change tracking period that strikes a balance between migration strategy needs and available resources on the on-premises database.
   > - Don't enable change tracking if you'll be running data upgrade on-premises, because it won't work.

2. [Create a full backup](/sql/relational-databases/backup-restore/create-a-full-database-backup-sql-server) of the on-premises production database. Differential or partial backups aren't supported as they don't include Change Tracking data required for replication runs.
3. Optionally, deploy the backup database to an Azure SQL Database for improved performance. See [Optimizing Cloud Migration Performance](migration-optimize-replication.md).
4. Complete the usual preparation steps on the backup on-premises database and address any issues that arise. Start the first [replication run](migrate-data-replication-run.md) and address any issues that arise.
5. Within the change tacking period set up on the on-premises production database in step 1, overwrite the backup database with a new full backup to replicate data that is new or modified since the backup created in step 2.

   > [!NOTE]
   > Rather than overwriting the backup, the old backup database can also be deleted. If creating a new backup rather than overwriting an existing backup, ensure the new backup database has the same name as the previous one. If the database name changes, run the Cloud Migration setup in the cloud environment again to point to the new database; the tooling will still attempt to use Change Tracking data if available to avoid replicating all data in the source database.
6. Repeat steps 2-5 as needed until you reach a state that is suitable for the final migration run.
7. Stop the usage of the on-premises environment ahead of the final backup of the on-premises production database. Run one final replication from the backup database to replicate the last data before running data upgrade.

   [!INCLUDE [bc-cloud-migrate-replicate-all-before-upgrade.md](../includes/bc-cloud-migrate-replicate-all-before-upgrade.md)]
8. Run [Data Upgrade](migration-data-upgrade.md) on the cloud environment.

   This step isn't required if you're on-premises version is the same as Business Central online (that is, both are the most current versions).

9. [Complete the migration](migration-finish.md) and go live on the cloud environment.

> [!IMPORTANT]
> Ensure the on-premises and cloud environments remain on the same Business Central version they were on when the cloud migration was set up. Do not update the on-premises environment and [reschedule updates](update-rollout-timeline.md#schedule-updates) to the cloud environment to a date after the cloud migration is completed.
>
> Avoid modifying the environment after the replication has been enabled. If you need to install or uninstall extensions or delete companies, disable the cloud migration, make the changes, then enable it again.

Keep in mind that the migration process can be complex, and issues might arise that require more troubleshooting. It's important to stay flexible and be prepared to adjust your migration strategy as needed to address any problems that arise.

## Schedule

- Plan the switch to use [!INCLUDE [prod_short](../includes/prod_short.md)] online for production carefully to not start until migration is complete  

  [!INCLUDE [bc-cloud-migrate-prod](../includes/bc-cloud-migrate-prod.md)]  

- Schedule the migration to not conflict with an update of [!INCLUDE [prod_short](../includes/prod_short.md)] online

  [!INCLUDE [bc-cloud-migrate-upgrade](../includes/bc-cloud-migrate-upgrade.md)]

## Next steps

- [Check prerequisites](cloud-migration-prerequisites.md)  
- [Optimizing cloud migration performance](migration-optimize-replication.md)  
- [Run data migration setup](migration-setup.md)
