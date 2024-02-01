---
title: Move an environment to another Microsoft Entra organization
description: You can move a Business Central environment to another Microsoft Entra tenant. Start in the Business Central admin center.
author: jswymer
ms.topic: conceptual
ms.devlang: al
ms.search.keywords: administration, tenant, admin, environment, move
ms.date: 04/01/2021
ms.author: jswymer
---

# Move an Environment to another Microsoft Entra organization

[!INCLUDE[azure-ad-to-microsoft-entra-id](~/../shared-content/shared/azure-ad-to-microsoft-entra-id.md)]

In some cases, the Microsoft Entra organization (also known as the Microsoft Entra tenant) of a [!INCLUDE[prod_short](../developer/includes/prod_short.md)] customer changes after they acquire a [!INCLUDE[prod_short](../developer/includes/prod_short.md)] environment. This situation can occur for various reasons, such as the following:

- Business entities merge.
- An acquisition takes place.
- The customer decides to use one Microsoft Entra tenant in a specific region and stop using Microsoft Entra tenants they created in other regions.
- The environment was mistakenly created by the reselling partner for the wrong Microsoft Entra tenant.

In all such cases, the customers want to preserve the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] environments they created for the original Microsoft Entra tenants, and link them to the new ones instead. Microsoft Support can move an environment from one Microsoft Entra tenant to another, based on a support request.

## Request to move an environment

As a partner, you can submit a support request to Microsoft Support by following the guidance at [Escalating support issues to Microsoft](manage-technical-support.md#escalating-support-issues-to-microsoft). When submitting these support requests, you must provide the following information:

- Proof of your delegated admin rights in both Microsoft Entra tenants
- Confirmation from the customer that the environment move is authorized by them

You can request to move one or more environments. For Microsoft to do the move, you'll need to provide information about the source and destination Microsoft Entra tenants, such as:

- Environments name, type and country
- Source tenant ID and domain
- Destination tenant ID and domain
- Does the destination tenant have a valid [!INCLUDE[prod_short](../developer/includes/prod_short.md)] subscription?
- Does the destination tenant have enough available user licenses?
- Does the destination tenant have enough environment licenses?
- Does the destination tenant have enough storage available for the environments being migrated?

Once the move is completed, your environments will appear in your new tenant.

## Considerations

- Environment data will remain unchanged during the move operation. The exact same environment will be linked to a specified Microsoft Entra tenant.
- The country, Azure region, and type of the environment (production or sandbox) will remain the same, and can't be changed during this operation.
- The operation will involve a downtime period for the environment being moved (typically not exceeding 2 hours). So the operation needs to be coordinated with the customer and Microsoft Support.
- [!INCLUDE[prod_short](../developer/includes/prod_short.md)] Support doesn't provide help with moving the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] subscriptions, domains, and other resources between the Microsoft Entra tenants. Your support representative or account manager will assist you in contacting billing to cancel or credit your previous subscription, if needed.

## Before you request your environment to be moved

- If you don't have a [!INCLUDE[prod_short](../developer/includes/prod_short.md)] subscription (paid or trial) in the destination tenant, you'll need to create one. You might need to purchase a new subscription in the destination tenant (or convert a trial to paid), if not already done.
- Make sure the destination tenant meets the following requirements:
  - It has at least as many active user licenses as the source tenant.
  - It has enough [!INCLUDE[prod_short](../developer/includes/prod_short.md)] environment add-on licenses to cover the environments being moved
  - It has at least as much [!INCLUDE[prod_short](../developer/includes/prod_short.md)] storage as the source tenant.

## After the environment has been moved

- Users may have been added to the environment prior to the move operation, while it was still connected to the old Microsoft Entra tenant. If so, these users won't be migrated to the new Microsoft Entra tenant. You'll need to recreate the users on the target tenant if you still want them. You can add multiple user accounts at once [using Excel spreadsheet or other file saved in CSV format](/microsoft-365/enterprise/add-several-users-at-the-same-time). After the users are created on the target Microsoft Entra tenant, assign them the required roles or licenses and [import these users into the moved environment](/dynamics365/business-central/ui-how-users-permissions).

  > [!NOTE] 
  > User personalizations will be lost.
- You might need to reconfigure some add-ins, external applications, and settings after the tenant-to-tenant migration. Some examples include the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] Outlook add-in, Excel add-in, Power BI, Power Apps, Power Automate connectors, Dataverse, user personalizations, and more.

## See also

[Managing Tenant Notifications](tenant-admin-center-notifications.md)
[Managing Apps](tenant-admin-center-manage-apps.md)
[Updating Environments](tenant-admin-center-update-management.md)
[Rename Environments](tenant-admin-center-environments-rename.md)
[Restoring an Environment](tenant-admin-center-backup-restore.md)
[Managing Production and Sandbox Environments](tenant-admin-center-environments.md)
[The Business Central Administration Center](tenant-admin-center.md)
[Introduction to automation APIs](itpro-introduction-to-automation-apis.md)
