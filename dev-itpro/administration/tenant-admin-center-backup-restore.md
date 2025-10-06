---
title: Restoring an environment in the admin center
description: Use the Business Central administration center to restore backups of environments. 
author: jswymer
ms.topic: how-to
ms.devlang: al
ms.search.keywords: administration, tenant, admin, environment, sandbox, restore, backup
ms.date: 01/30/2025
ms.author: jswymer
ms.reviewer: jswymer
---

# Restoring an environment in the admin center

As an administrator, you can restore an existing environment from a time in the past, within the retention period that applies to both production and sandbox environments.  

Database backups are an essential part of any business continuity and disaster recovery strategy, because they protect your data from corruption or deletion. [!INCLUDE[prod_short](../developer/includes/prod_short.md)] online uses Azure SQL Database as the underlying database backup technology for its environments. All databases are protected by automated backups that the Azure SQL service continuously creates and maintains. For more information, see [Business continuity and disaster recovery (BCDR)](../service-overview.md#business-continuity-and-disaster-recovery-bcdr).  

## Users who can restore environments

Permission to restore environments is limited to specific types of users: internal and delegated administrators. The following users are allowed to restore environments.

- Delegated administrators. For more information, see [Delegated administrator access to Business Central Online](delegated-admin.md)
- Administrators from the organization that subscribes to [!INCLUDE [prod_short](../developer/includes/prod_short.md)] online

Also, these users must have the **D365 BACKUP/RESTORE** permission set assigned to their user account in the environment they're trying to export.

For more information about permissions sets and user groups, see [Assign Permissions to Users and Groups](/dynamics365/business-central/ui-define-granular-permissions).

## Considerations and limitations

- Environments can only be restored if the customer has a paid [!INCLUDE[prod_short](../developer/includes/prod_short.md)] subscription.
- Each environment can be restored up to 10 times in a calendar month.
- An environment can be restored to any time up to 28 days ago. It's not possible to restore an environment to a time more than 28 days ago.
- An environment can only be restored within the same Azure region and country/region ([!INCLUDE[prod_short](../developer/includes/prod_short.md)] localization) as the original environment.
- A production environment can be restored to an environment of type **Production** or **Sandbox**. A sandbox environment can only be restored to a **Sandbox** environment.
- When you restore a sandbox environment, all development extensions (that is, extensions published directly from Visual Studio Code) aren't available in the restored environment&mdash;even if they were present at the point-in-time you're restoring to). Additionally, any per-tenant extensions that depend on such development extensions are also not available.
- Every AppSource and [!INCLUDE[prod_short](../developer/includes/prod_short.md)] app in the restored environment will have the latest available hotfix installed automatically&mdash;even if the hotfix was introduced after the point-in-time you're restoring to. The environment is restored to the major/minor version it was on at the time you're restoring to.
- Microsoft Entra app registration, status, and permissions in the environment are restored to their state at the time you're restoring to. Apps that were authorized in the [!INCLUDE [prodadmincenter](../developer/includes/prodadmincenter.md)] aren't restored even if their permissions in the restored environment are.
- The update window and application insights connection string specified for the source environment in the admin center at the time when the restore operation started will be retained on the target environment. The target environment won't be restored to the values for these settings that existed on the source environment at the time that the source environment is being restored to.
- Power Platform environments that are [linked](tenant-admin-center-environments.md#linked-power-platform-environment) to the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] environment you're restoring aren't affected by this operation. The Power Platform environment won't be restored, and the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] environment created as part of the restore operation won't be linked to any Power Platform environment.
- If the environment is encrypted using a [customer-managed encryption key](../security/security-online.md#customer-managed-encryption-key) inherited from a [linked](tenant-admin-center-environments.md#linked-power-platform-environment) Power Platform environment, the new environment created by the restore operation will be encrypted using a Microsoft-managed encryption key. To encrypt the newly created environment using a customer-managed encryption key link it to a Power Platform environment that has the desired customer-managed encryption key applied.
- [Early access preview environments](preview-environments.md) are automatically updated to a new preview build every Sunday. It is not possible to restore the environment to a previous preview build, limiting the period for which the environment can be restored.

## Environment cleanup

When you restore an environment, the following environment setups and integration data are cleaned up to avoid unexpected behavior with external integrations. You can skip this cleanup by ticking the box under **Advanced Options** in the Admin Center.

[!INCLUDE [create copy-restore-cleanup-operations](../developer/includes/copy-restore-cleanup-operations.md)]

## Before you restore an environment

Here are a few important things to do when you're planning to restore an environment:

- Make sure you communicate the plan to restore an environment within your organization upfront, in good time.

- Typically, you want to stop users and external integrations from using the environment during restoration. Consider doing the following actions in the environment you're planning to restore:

  - Remove access to the environment for nonessential users, but make sure required users, like administrators, keep access. For more information, see [Remove a user's access to the system](/dynamics365/business-central/ui-how-users-permissions#to-remove-a-users-access-to-the-system).

  - Put all job queues to on hold. For more information, see [Use Job Queues to Schedule Task](/dynamics365/business-central/admin-job-queues-schedule-tasks).

- Consider renaming the environment. The users and external integrations won't be able to access it by its old name.  

  When restoring an environment, you'll create a new environment that the database backup will be restored to. You can't use the same name for two environments of the same customer. So if you want the restored environment to have the same name as the original environment, rename the original environment before you run the restore operation. For example, you could change the name to include **DONOTUSE**.

  For more information, see [Rename Environments in the Admin Center](tenant-admin-center-environments-rename.md).

## Restore an environment

To restore an environment, you'll have to provide a name for the environment and a date/time from which to restore the database.

1. Select **Environments** and then open the environment you want to restore.
2. Select **Restore**.
3. In the **Restore Environment** pane, specify the date and time in the past to which you want to restore the environment. <!-- uncomment when feature is deployed A note will indicate to what version your environment will be restored if your environment has been updated since the time you are restoring to. -->
4. Select the type to be used for the restored environment.
5. Specify a name for the restored environment.
6. Select **Restore**.

    > [!NOTE]
    > For newly created environments it may take up to 30 min for the backups to be initialized, so you may not be able to restore an environment if you have just created it. 
7. Under **Advanced Options**, select whether you want to uninstall per-tenant extensions, non-Microsoft AppSource apps, or skip environment cleanup as part of this restore.

   > [!NOTE]
   > In some cases, extension compilation issues may prevent you from restoring your environment. If you don't need installed extensions to be restored, you can uninstall them as part of the environment restore to avoid compilation errors. By default, we disable environment setups and clean up integration data listed previisly under **Considerations and limitations**. By skipping environment cleanup you can override this default behavior.

8. When the process starts, you can go to the list of your environments and see the status of the restored environment. At first, you'll see the new environment with state **Preparing**. The original environment state remains as **Active**.

   Several factors affect the restore operation duration. For large or highly active databases, the restore might take several hours. You can find more details about the factors that affect the recovery time at [Recovery time](/azure/azure-sql/database/recovery-using-backups#recovery-time).  

   Once the restore is completed, the environment state changes to **Active**.  If the restore operation fails, you can find the failure details on the **Operations** page. In this case, delete the failed environment, and then try to restore again. Contact Microsoft Support if the issue persists.

## After you restore an environment

After restoring an environment, you should inspect and adjust data to prepare it for users. Consider enforcing these steps during this period:

- Remove access to the environment for nonessential users, but make sure required users, like administrators, keep access.
- Put all job queues in the restored environment to on hold immediately after restore. For more information, see [View Scheduled Tasks](/dynamics365/business-central/admin-job-queues-schedule-tasks#view-scheduled-tasks) in the business functionality content.
- If needed, you can upload the per-tenant extensions targeting the next version of [!INCLUDE[prod_short](../developer/includes/prod_short.md)] again.

The original environment remains available and isn't affected by the restore operation. You can then get back to the original environment if you need to look up data. Or maybe you have to migrate some data to the restored environment. You can, for example, migrate data by using [!INCLUDE[prod_short](../developer/includes/prod_short.md)] RapidStart services. For more information, see [Migrate Customer Data](/dynamics365/business-central/admin-migrate-customer-data).

> [!IMPORTANT]
> You can restore your production environment into a new production environment even if doing so results in exceeding your number of environments or database capacity quotas. You can however only exceed this quota by one extra production environment, regardless of how many production environments you have available for your subscription. This capability is provided as an exception, to ensure that you can always restore your production environment in critical situations. You must return within your quota within 30 days following the restore by either removing the original production environment or by purchasing an additional production environment. Before removing the environment, we recommend you [export the environment to an Azure storage container](tenant-admin-center-database-export.md) in case you need to access some data at a later point. This exception isn't available for restoring from and to sandbox environments.

When you're satisfied with the data in the restored database, enable the users, start the job queues, and let your organization know that the restore process is now completed and they can again use the environment.

## Related information

[Managing Tenant Notifications](tenant-admin-center-notifications.md)  
[Managing Apps](tenant-admin-center-manage-apps.md)  
[Updating Environments](tenant-admin-center-update-management.md)  
[Rename Environments](tenant-admin-center-environments-rename.md)  
[Restoring an Environment](tenant-admin-center-backup-restore.md)  
[Move an Environment to another Microsoft Entra organization](tenant-admin-center-environments-move.md)  
[The Business Central Administration Center](tenant-admin-center.md)  
[Introduction to automation APIs](itpro-introduction-to-automation-apis.md)  
[Service Overview for Business Central Online](../service-overview.md)  
