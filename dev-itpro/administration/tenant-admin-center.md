---
title: Business Central Administration Center
description: Learn about how a VAR or an internal administrator can set update windows and other admin tasks using the admin center.  
author: jswymer
ms.topic: article
ms.devlang: al
ms.search.keywords: administration, tenant, admin, environment, telemetry
ms.date: 06/20/2025
ms.author: jswymer
ms.reviewer: jswymer
---
# The Business Central administration center

[!INCLUDE[azure-ad-to-microsoft-entra-id](~/../shared-content/shared/azure-ad-to-microsoft-entra-id.md)]

The [!INCLUDE[prodadmincenter](../developer/includes/prodadmincenter.md)] provides a portal for administrators to do administrative tasks for a [!INCLUDE[prod_short](../developer/includes/prod_short.md)] tenant. Some of the tasks that administrators can do include:

- [View and work with production and sandbox environments](tenant-admin-center-environments.md) on the tenant.
- [Set up notification recipients](tenant-admin-center-notifications.md).
- [Manage environment access](tenant-admin-center-manage-access.md).
- [Set up Application Insights telemetry](telemetry-enable-application-insights.md).

> [!div class="mx-imgBorder"]
> ![Screenshot of the Business Central admin center.](../developer/media/admin/business_central_admin_center.png)

## Supported Microsoft Entra roles for access

Users with at least the following [Microsoft Entra roles](/entra/identity/role-based-access-control/permissions-reference) are authorized to access the [!INCLUDE[prodadmincenter](../developer/includes/prodadmincenter.md)] and [!INCLUDE [prod_short](../developer/includes/prod_short.md)] environments:

- [Dynamics 365 Administrator](/entra/identity/role-based-access-control/permissions-reference#dynamics-365-administrator)
- [Dynamics 365 Business Central Administrator](/entra/identity/role-based-access-control/permissions-reference#dynamics-365-business-central-administrator)

Although the following roles aren't required to access the [!INCLUDE[prodadmincenter](../developer/includes/prodadmincenter.md)] or its environments, they allow for administration of tools and resources that integrate with [!INCLUDE [prod_short](../developer/includes/prod_short.md)]:

- [Power Platform Administrator](/entra/identity/role-based-access-control/permissions-reference#power-platform-administrator) - create and manage all aspects of Power Platform environments.
- [Service Support Administrator](/entra/identity/role-based-access-control/permissions-reference#service-support-administrator) - create and manage support requests.
- [Message Center Reader](/entra/identity/role-based-access-control/permissions-reference#message-center-reader) - read notifications in [Message Center](/microsoft-365/admin/manage/message-center) and sign up for email notifications.
- [Cloud Application Administrator](/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator) - create and manage all aspects of enterprise applications and application registration, for example to manage applications that interact with the Business Central and Admin Center APIs.
- [Conditional Access Administrator](/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator) - manage conditional access settings, for example to specify access policies for authentications to the [!INCLUDE [prod_short](../developer/includes/prod_short.md)] application.
- [License Administrator](/entra/identity/role-based-access-control/permissions-reference#license-administrator) - add, remove, and update license assignments on users and groups.

## Internal administrators

As the internal administrator, you can select the link in the **Settings** menu when you're signed in to [!INCLUDE [prod_short](../developer/includes/prod_short.md)].  

Alternatively, you can access the administration center from the URL, use the following pattern but replace *[TENANT_ID]* with the tenant ID of your [!INCLUDE [prod_short](../developer/includes/prod_short.md)]:

`https://businesscentral.dynamics.com/[TENANT_ID]/admin`

> [!TIP]
> The tenant ID is shown in the **Help and Support** page in your [!INCLUDE [prod_short](../developer/includes/prod_short.md)].  

## Delegated administrators (Partner users)

Partner organizations can set up a [Granular Delegated Administration Privileges (GDAP)](/partner-center/gdap-introduction) relationship including at least one of the Microsoft Entra roles that grant access to the [!INCLUDE[prodadmincenter](../developer/includes/prodadmincenter.md)] to access their customers' administration centers. Learn how to set up a GDAP relationship in [Obtain granular admin permissions to manage a customer's service](/partner-center/gdap-obtain-admin-permissions-to-manage-customer).

After the relationship is set up, users in the partner tenant can access the [!INCLUDE[prodadmincenter](../developer/includes/prodadmincenter.md)] for the customer's tenant. However, the users must be in a security group assigned to at least one of the required roles in the active GDAP relationship, which is done by completing these steps:

1. Sign in to the [Partner Dashboard](https://partnercenter.microsoft.com/dashboard).
2. Select the **Customers** link in the navigation pane.
3. Select the customer tenant that you want to do administrative tasks for.
4. Select **Service Management**.
5. Under the **Administer Services** heading, select [!INCLUDE[prod_long](../developer/includes/prod_long.md)].

Kearn more in [Grant granular permissions to security groups](/partner-center/customers/gdap-assign-microsoft-entra-roles#grant-permissions-to-security-groups).

> [!TIP]
> Delegated administrators don't need a license assigned or be a guest user in the customer tenant to access and administer the customer's [!INCLUDE [prod_short](../developer/includes/prod_short.md)] environments.

As a delegated admin, you get to the administration center by using the URL of a tenant like internal admins, as described in the previous section. In the [!INCLUDE [prodadmincenter](../developer/includes/prodadmincenter.md)], you can [specify support information](../technical-support.md#configuring-the-support-experience), create and remove [environments](tenant-admin-center-environments.md), and you can access your customer's [!INCLUDE [prod_short](../developer/includes/prod_short.md)] environments.

> [!NOTE]
> As the partner, there are certain tasks that you can't do in your customers' [!INCLUDE [prod_short](../developer/includes/prod_short.md)]. For more information, see [Administration as a partner](tenant-administration.md#administration-as-a-partner).

### Cleaning up settings

If your organization decides to switch to another partner, you must make sure that some settings that your current partner made in the [!INCLUDE [prodadmincenter](../developer/includes/prodadmincenter.md)] are removed. This task includes the following settings:

- Support contact details

    1. In the [!INCLUDE [prodadmincenter](../developer/includes/prodadmincenter.md)], select the relevant environment, and then, in the **Support** menu, select **Manage Support Contact**.
    2. Verify that the values in the **Name**, **Email address**, and the **Website** fields are still relevant; if not, then delete or modify the values.

- Notification recipients

    1. In the [!INCLUDE [prodadmincenter](../developer/includes/prodadmincenter.md)], on the left side, select **Notification recipients**
    2. Verify that the list of email addresses are still relevant; if not, then delete or modify the values.

- Application Insights key (if set up by the partner)

    1. In the [!INCLUDE [prodadmincenter](../developer/includes/prodadmincenter.md)], select the relevant environment, and then, in the top menu, select **Application Insights Key**.
    2. Remove the value of the **Instrumentation Key**

- Authorized Microsoft Entra apps (if set up by the partner)

    1. In the [!INCLUDE [prodadmincenter](../developer/includes/prodadmincenter.md)], navigate to 'Authorized Microsoft Entra apps' and remove any apps authorized by the partner.
    2. Revoke consent granted to the Microsoft Entra app belonging to the partner from your Microsoft Entra tenant. For more information, [see here](/azure/active-directory/manage-apps/manage-application-permissions).
    3. Removed apps might have extra permissions assigned to execute certain administration operations, such as the **D365 BACKUP/RESTORE** permission. Any apps set up with permissions in Business Central can be disabled from the **Microsoft Entra applications** page. For more information, [Assign Permissions to Users and Groups](/dynamics365/business-central/ui-define-granular-permissions).

When you establish a relationship with a new partner, they fill in these fields again.

## Related information

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
