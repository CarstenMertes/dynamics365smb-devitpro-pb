---
title: Managing Sessions in the Admin Center
description: Use the Business Central administration center to manage sessions in your tenant environments. 
author: jswymer
ms.topic: conceptual
ms.devlang: al
ms.search.keywords: administration, tenant, admin, environment, sandbox, sessions
ms.date: 12/14/2021
ms.author: jswymer
---

# Managing Sessions in the Admin Center

[!INCLUDE[azure-ad-to-microsoft-entra-id](~/../shared-content/shared/azure-ad-to-microsoft-entra-id.md)]

For each environment in the [!INCLUDE[prodadmincenter](../developer/includes/prodadmincenter.md)], you can use the **Manage Sessions** page to view information about active sessions on an environment and cancel selected sessions.

To open the page, select **Manage Sessions**. Use the **Show session details** check box to show more or fewer details.

## Cancel sessions

Canceling a session is sometimes the only way to unblock a customer. For example, a long-running report is locking data in a table, preventing warehouse employees from working.

To cancel a session, select it from the list and then select **Cancel selected sessions**.  

## Restart environment

In some cases, canceling the sessions does not solve the problem. In those cases, you may want to restart the environment.  

To restart an environment that is causing problems for you, go to the **Manage Sessions** page, choose the relevant environment, and then choose the **Restart Environment** action.  

> [!IMPORTANT]
> Make sure that all users are signed out of all companies in the environment before you restart it.

## See also

[Managing Tenant Notifications](tenant-admin-center-notifications.md)  
[Managing Apps](tenant-admin-center-manage-apps.md)  
[Updating Environments](tenant-admin-center-update-management.md)  
[Rename Environments](tenant-admin-center-environments-rename.md)  
[Restoring an Environment](tenant-admin-center-backup-restore.md)  
[Move an Environment to another Microsoft Entra organization](tenant-admin-center-environments-move.md)  
[Introduction to automation APIs](itpro-introduction-to-automation-apis.md)  
