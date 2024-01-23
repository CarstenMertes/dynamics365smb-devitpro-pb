---
title: "Licensing in Business Central"
author: jswymer
description: Provides an overview of the licensing in Business Central
ms.reviewer: na
ms.topic: conceptual
ms.author: jswymer
ms.date: 03/23/2022
---

# Licensing in Dynamics 365 Business Central

[!INCLUDE[azure-ad-to-microsoft-entra-id](~/../shared-content/shared/azure-ad-to-microsoft-entra-id.md)]

[!INCLUDE[prod_short](../developer/includes/prod_short.md)] licenses can only be purchased through CSP. Microsoft offers several types of paid licenses for business users:

- Essential  
- Premium  
- Team Member  
- External Accountant  
- Microsoft also offers read-only access to [!include[prod_short](../developer/includes/prod_short.md)] through Microsoft 365 licenses, as an addition to Premium or Essentials plans

Prospects and customers can also subscribe for an evaluation version by using self-service sign-up, also known as the viral trial. This subscription comes with 10,000 licenses, and partners can use such viral trials to let prospects explore [!INCLUDE [prod_short](../includes/prod_short.md)] using non-production companies. For more information, see [Preparing Demonstration Environments of [!INCLUDE[prod_long](../developer/includes/prod_long.md)]](../administration/demo-environment.md).  

[!INCLUDE [admin-license-trial](../includes/admin-license-trial.md)]

[!include[prod_short](../developer/includes/prod_short.md)] online doesn't use the classic [!INCLUDE [navnow_md](../developer/includes/navnow_md.md)] license files (.flf). Instead, permissions are generated based on entitlements.  

Behind the scenes, the **Entitlements** table defines license permissions per object. Entitlements are grouped in the **Entitlement Set** table, and then each entitlement set is associated with one of the four Microsoft Entra ID service plans.  

This condition means that when a user purchases, for example, an Essential license and tries to sign in to Business Central, we retrieve the user's service plan (in this case Essential) from Microsoft Entra ID. Then, we load the corresponding entitlements as license permissions.  

> [!NOTE]
> For more information about the different types of licenses and how licensing works in [!INCLUDE[prod_short](../developer/includes/prod_short.md)], see the Dynamics 365
Licensing Guide, which you can download from [https://go.microsoft.com/fwlink/?LinkId=866544](https://go.microsoft.com/fwlink/?LinkId=866544).

## Entitlements and user groups

*Entitlements* are permissions that describe which objects in [!INCLUDE [prod_short](../developer/includes/prod_short.md)] a user is entitled to use according to their Microsoft Entra role or the license they purchased from Microsoft.  

The **User Group Plan** table stores the mapping between the service plans and the user groups. Based on this mapping, the service determines which user group is assigned to a user by default when a user logs in to [!INCLUDE [prod_short](../developer/includes/prod_short.md)] for the first time. The user group assigns a specific license (or makes the user a member of a specific Microsoft Entra role).  

When a user logs in to [!INCLUDE [prod_short](../developer/includes/prod_short.md)], the service applies the intersection of the entitlements that are associated with the user's service plan (or Microsoft Entra role) and the permissions that are defined for that user. Entitlements always have higher priority over permissions. For example, even is the user is given SUPER permissions by the admin but has the Team Member license assigned – the user can still only access the objects defined by the Team Member entitlements.  

You can verify how entitlements, licenses, and user groups work together by looking at the **Effective Permissions** page, which you can access from the **User** page. Starting with 2022 release wave 1, admins can also customize the default permissions per license type. For more information, see [Create Users According to Licenses](/dynamics365/business-central/ui-how-users-permissions) in the business functionality content for [!INCLUDE [prod_short](../developer/includes/prod_short.md)].  

### Entitlements in production and sandbox environments

In versions earlier than 2020 release wave 2 (version 17.0), entitlements are only enforced in production environments so that prospective and existing customers could explore the functionality of the Premium subscription in a sandbox environment without having to purchase a Premium license.  

However, partners that create and test their extensions using sandbox environments of that type could miss errors in their code that would be related to entitlements or access, so that those issues wouldn't be found until they deployed their extensions to the production environments. But since 2020 release wave 2, the license checks for entitlements are now also enforced in the sandbox environments.  

Now, you can explore such functionality by creating an evaluation company in either a production or a sandbox environment using the free evaluation subscription that is available from [https://dynamics.microsoft.com/business-central](https://dynamics.microsoft.com/business-central/overview).  Alternatively, you can use the **Business Central Premium - Trial** subscription that is available through the CSP program as described [here](customer-signup.md#premiumtrial). By using these subscription types, customers and partners can explore the capabilities included with the Premium subscription.  

## Reassigning licenses

The licensing terms in the [Online Services Terms](https://www.microsoft.com/licensing/product-licensing/products) document don't allow temporary assignment of a license that belongs to one user to another user.

Most, but not all, licenses can be reassigned. Except as permitted in this paragraph or in the Online Service-specific Terms, the customer can't reassign a license on a short-term basis, meaning within 90 days of the latest assignment. The customer can reassign a license on a short-term basis to cover a user's absence or the unavailability of a device that is out of service. Reassignment of a license for any other purpose must be permanent. When a customer reassigns a license from one device or user to another, they must block access and remove any related software from the former device or from the former user's device.

## Device licenses

The Dynamics 365 Business Central Device license allows multiple users to simultaneously use a device that is covered by the license. For example, it might be a point of sales, shop floor, or warehouse device. When you've purchased many device licenses, up to that number of users assigned to the *Dynamics 365 Business Central Device Users* group can sign in at the same time. For more information, see the Microsoft Dynamics 365 Business Central Licensing Guide. The guide is available for download on the [Business Central](https://dynamics.microsoft.com/business-central/overview/) website.

Your company's Microsoft 365 administrator or Microsoft partner can create the *Dynamics 365 Business Central Device Users* group and add device users as members in the [Microsoft 365 Admin Center](https://admin.microsoft.com/) or on the [Azure portal](https://portal.azure.com/).

### Device user features and limitations

Users with the Device license can now set up jobs to run as scheduled tasks in the job queue of [!INCLUDE [prod_short](../developer/includes/prod_short.md)]. Device users are concurrent users and when it's time to run their scheduled tasks, they'll be automatically signed in to run their tasks in background sessions. When their tasks are running, each of them is considered present in the system and using a device license. 

In terms of limitations, a device user can't be the first user to sign in. A user of type Administrator, Full User, or External Accountant must be the first to sign in so they can set up [!INCLUDE [prod_short](../developer/includes/prod_short.md)]. For more information, see [Administration of Business Central Online](../administration/tenant-administration.md).  

### To create the Dynamics 365 Business Central Device Users group

1. In the Microsoft 365 Admin Center, go to the **Groups** page.
2. Choose the **Add a group** action.
3. On the **Choose a group type** page, choose the **Security** option, and then choose the **Add** action.
4. On the **Basics** page, enter *Dynamics 365 Business Central Device Users* as the name of the group.
  
   >[!NOTE]
   >The name of the group must be spelled in English exactly as shown in step 4, even if you are using another language. If you have copied the name of the group from a document, such as a PDF, verify that the name does not contain extra spaces.
5. Choose the **Close** button.

> [!NOTE]
> You can also create a group of type Microsoft 365. For more information, see [Compare Groups](/microsoft-365/admin/create-groups/compare-groups)

### To add members to the group

1. In the Microsoft 365 Admin Center, refresh the **Groups** page so your new group appears.
2. Select the **Dynamics 365 Business Central Device Users** group, and then choose the **View all and manage members** action.
3. Choose the **Add members** action.
4. Select the users that you want to add, and then choose the **Save** button.
5. Choose the **Close** button three times.

You can add as many users to the *Dynamics 365 Business Central Device Users* group as you need. However, the number of devices that users can simultaneously sign in to is defined by the number of purchased device licenses.

> [!NOTE]
> You do not need to assign a [!INCLUDE [prod_short](../developer/includes/prod_short.md)] license to users that are members of the *Dynamics 365 Business Central Device Users* group.

## Microsoft 365 licenses 

Microsoft 365 users can access [!INCLUDE [prod_short](../developer/includes/prod_short.md)] data in Microsoft Teams, using only their Microsoft 365 license. This capability is intended for employees across the organization to participate in team decisions and collaboration when Business Central records are shared with them.

For a detailed overview of the use rights, minimum requirements and which Microsoft 365 plans are supported, see [Business Central Access with Microsoft 365 Licenses](/dynamics365/business-central/admin-access-with-m365-license).

## See Also  

[Get Started as a Reseller of Business Central Online](../administration/get-started-online.md)  
[Deployment of [!INCLUDE[prod_long](../developer/includes/prod_long.md)]](Deployment.md)  
[Working with Sandboxes and Entitlements](../developer/devenv-work-sandbox-entitlements.md)  
[[!INCLUDE[embedapp](../developer/includes/embedapp.md)] Overview](embed-app-overview.md)  
