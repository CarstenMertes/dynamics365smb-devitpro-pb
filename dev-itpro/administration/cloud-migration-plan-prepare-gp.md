---
title: Prepare and plan for cloud migration from Dynamics GP
description: This article provides recommendations to help you define your cloud migration strategy and get environments and users ready for Dynamics GP cloud migration.
author: jswymer
ms.author: jswymer
ms.reviewer: jswymer
ms.topic: conceptual
ms.date: 02/19/2024
ms.custom: bap-template 
---
# Prepare and plan for cloud migration from Dynamics GP

This article provides recommendations to help you define your cloud migration strategy and get environments and users ready for cloud migration.

## Run migration assessment tool

The migration assessment tool delivers valuable insight into your overall readiness to migrate. It provides migration options based on your needs, and detects potential migration issues based on your Dynamics GP system structure. To get started with the migration tool, go to [https://bcmigrationassessments.com/](https://bcmigrationassessments.com/).

Learn more about the tool in the video [Are You Ready for Business Central](https://www.youtube.com/watch?v=r2gNgQrCgoo&list=PLcakwueIHoT9yVFOV6_BXMVeodPq3lt3o&index=15).

## Determine what data to migrate

The data that's migrated is determined on a per-company basis. When a company is migrated, data in company-specific tables of base application is migrated. 

You can choose to migrate data for all companies or only specific companies. It's recommended to determine which companies to migrate upfront to save time and resources. Keep in mind that the more companies you replicate in a single operation, the longer the migration takes.

[!INCLUDE [migrate-limits](../developer/includes/migrate-limits.md)]

## Determine your migration approach

It's important to have a solid migration strategy in place to ensure a smooth transition. Most migrations can run from the on-premises production database with minimal downtime for end users. However, for especially large migrations, it might be better to run migration from a backup of the on-premises database<!--deployed as Azure SQL Database-->. Doing migrations this way improves migration speeds and minimizes performance loss and downtime on the on-premises production database. The following steps outline a typical migration approach.

1. Move Dynamics GP database to Azure Data Lake (optional).

   You can create a copy of the Dynamics GP database in Azure Data Lake so that you have it for future reference after the migration to [!INCLUDE [prod_short](../developer/includes/prod_short.md)] online. [Learn more](cloud-migration-azure-data-lake-gp.md).
1. [Create a full backup](/sql/relational-databases/backup-restore/create-a-full-database-backup-sql-server) of the on-premises production database. Differential or partial backups aren't supported as they don't include Change Tracking data required for replication runs.
1. Complete the usual preparation steps on the backup on-premises database and address any issues that arise.
1. Complete the cloud migration setup, including choosing the companies to migrate.
1. Run the [replication](migrate-data-replication-run.md) and address any issues that arise.
1. Stop the usage of the on-premises environment ahead of the final backup of the on-premises production database. 
1. Run [Data Upgrade](migration-data-upgrade.md) on the cloud environment.
1. [Complete the migration](migration-finish.md) and go live on the cloud environment.

> [!IMPORTANT]
> Ensure the on-premises and cloud environments remain on the same <!--Business Central version--> they were on when the cloud migration was set up. Do not update the on-premises environment and [reschedule updates](update-rollout-timeline.md) to the cloud environment to a date after the cloud migration is completed.
>
> Avoid modifying the environment after the replication has been enabled. If you need to install or uninstall extensions or delete companies, disable the cloud migration, make the changes, then enable it again.

Keep in mind that the migration process can be complex, and issues might arise that require more troubleshooting. It's important to stay flexible and be prepared to adjust your migration strategy as needed to address any problems that arise.

## Schedule

- Plan the switch to use [!INCLUDE [prod_short](../includes/prod_short.md)] online for production carefully to not start until migration is complete  

  [!INCLUDE [bc-cloud-migrate-prod](../includes/bc-cloud-migrate-prod.md)]  

- Schedule the migration to not conflict with an update of [!INCLUDE [prod_short](../includes/prod_short.md)] online

  [!INCLUDE [bc-cloud-migrate-upgrade](../includes/bc-cloud-migrate-upgrade.md)]

## Next steps

- [Check prerequisites](cloud-migration-prerequisites-gp.md)  
- [Optimizing cloud migration performance](migration-optimize-replication.md)  
- [Run data migration setup](migration-setup.md)
