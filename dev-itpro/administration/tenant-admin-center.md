---
title: Business Central Admin Center| Microsoft Docs
description: Learn about how a VAR or an internal administrator can set update windows and other admin tasks.  
author: jswymer
ms.topic: conceptual
ms.devlang: al
ms.search.keywords: administration, tenant, admin, environment, telemetry
ms.date: 04/01/2021
ms.author: jswymer
---
# The Business Central Administration Center

[!INCLUDE[azure-ad-to-microsoft-entra-id](~/../shared-content/shared/azure-ad-to-microsoft-entra-id.md)]

The [!INCLUDE[prodadmincenter](../developer/includes/prodadmincenter.md)] provides a portal for administrators to do administrative tasks for a [!INCLUDE[prod_short](../developer/includes/prod_short.md)] tenant. Here, administrators can:

- [view and work with production and sandbox environments](tenant-admin-center-environments.md) for the tenant.
- [set up upgrade notifications](tenant-admin-center-notifications.md).
- [view telemetry](tenant-admin-center-telemetry.md) for events on the tenant.  

> [!div class="mx-imgBorder"]
> ![Business Central Admin Center.](../developer/media/admin/business_central_admin_center.png)

## Access to the administration center

Users with the following Microsoft Entra roles are authorized to access the [!INCLUDE[prodadmincenter](../developer/includes/prodadmincenter.md)]:

- Global Administrator
- Dynamics 365 Administrator
- Helpdesk Administrator (Delegated users only)

## Internal administrators

As the internal administrator, you can choose the link in the **Settings** menu when you're signed in to [!INCLUDE [prod_short](../developer/includes/prod_short.md)].  

Alternatively, you can access the administration center from the URL, use the following pattern but replace *[TENANT_ID]* with the tenant ID of your [!INCLUDE [prod_short](../developer/includes/prod_short.md)]:

`https://businesscentral.dynamics.com/[TENANT_ID]/admin`

> [!TIP]
> The tenant ID is shown in the **Help and Support** page in your [!INCLUDE [prod_short](../developer/includes/prod_short.md)].  
  
In the administration center, you can [create and monitor environments](tenant-admin-center-environments.md). This is also where you manage the people who must be [notified of administrative events](tenant-admin-center-notifications.md) for your tenant.  

Your partner can help you set up telemetry for production environments, including [integration with Application Insights in Azure](tenant-admin-center-telemetry.md).  

### Cleaning up settings

If your organization decides to switch to another partner, you must make sure that some settings that your current partner made in your [!INCLUDE [prodadmincenter](../developer/includes/prodadmincenter.md)] are removed. This includes the following settings:

- Support contact details

    1. In the [!INCLUDE [prodadmincenter](../developer/includes/prodadmincenter.md)], choose the relevant environment, and then, in the **Support** menu, choose **Manage Support Contact**.
    2. Verify that the values in the **Name**, **Email address**, and the **Website** fields are still relevant; if not, then delete or modify the values.

- Notification recipients

    1. In the [!INCLUDE [prodadmincenter](../developer/includes/prodadmincenter.md)], on the left side, choose **Notification recipients**
    2. Verify that the list of email addresses are still relevant; if not, then delete or modify the values.

- Application Insights key (if this was set up by the partner)

    1. In the [!INCLUDE [prodadmincenter](../developer/includes/prodadmincenter.md)], choose the relevant environment, and then, in the top menu, choose **Application Insights Key**.
    2. Remove the value of the **Instrumentation Key**

- Authorized Microsoft Entra apps (if this was set up by the partner)

    1. In the [!INCLUDE [prodadmincenter](../developer/includes/prodadmincenter.md)], navigate to 'Authorized Microsoft Entra apps' and remove any apps authorized by the partner.
    2. Revoke consent granted to the Microsoft Entra app belonging to the partner from your Microsoft Entra tenant. For more information, [see here](/azure/active-directory/manage-apps/manage-application-permissions).
    3. Removed apps may have additional permissions assigned to execute certain administration operations, such as the **D365 BACKUP/RESTORE** permission. Any apps set up with permissions in Business Central can be disabled from the **Microsoft Entra applications** page. For more information, [Assign Permissions to Users and Groups](/dynamics365/business-central/ui-define-granular-permissions).

When you establish a relationship with a new partner, they will fill in these fields again.

## Partner access to the administration center

As a partner, you can access the administration center from the Partner Dashboard in the Microsoft Partner Center:

1. Log into the [Partner Dashboard](https://partnercenter.microsoft.com/dashboard).
2. Select the **Customers** link in the navigation pane.
3. Select the customer tenant that you want to do administrative tasks for.
4. Select **Service Management**.
5. Under the **Administer Services** heading, select [!INCLUDE[prod_long](../developer/includes/prod_long.md)].

You can also get to the administration center by using the URL of a tenant, as described in the previous section.

In the [!INCLUDE [prodadmincenter](../developer/includes/prodadmincenter.md)], you can [specify support information](../technical-support.md#configuring-the-support-experience), create and remove [environments](tenant-admin-center-environments.md), and [submit support request](manage-technical-support.md#escalating-support-issues-to-microsoft) for your customer.  

From the [!INCLUDE [prodadmincenter](../developer/includes/prodadmincenter.md)], you can access your customer's [!INCLUDE [prod_short](../developer/includes/prod_short.md)] for troubleshooting, for example.  

> [!NOTE]
> As the partner, there are certain tasks that you cannot do in your customers' [!INCLUDE [prod_short](../developer/includes/prod_short.md)]. For more information, see [Acting as a delegated administrator](tenant-administration.md#acting-as-a-delegated-administrator).

## See also

[Production and Sandbox Environments](environment-types.md)  
[Managing Environments](tenant-admin-center-environments.md)  
[Tenant Notifications](tenant-admin-center-notifications.md)  
[Environment Telemetry](tenant-admin-center-telemetry.md)  
[Administration Center API](administration-center-api.md)  
[Managing Technical Support](manage-technical-support.md)  
[Business Central Data Security](../security/data-security.md)  
[Introduction to automation APIs](itpro-introduction-to-automation-apis.md)  
[Microsoft Partner Dashboard](https://partnercenter.microsoft.com/dashboard)  
[Add a new customer in the Partner Center](/partner-center/add-a-new-customer)  
[Assign licenses to users in the Partner Center](/partner-center/assign-licenses-to-users)  
[Create new subscriptions in the Partner Center](/partner-center/create-a-new-subscription)  
[Cloud Solution Provider program - selling in-demand cloud solutions](/partner-center/csp-overview)  
