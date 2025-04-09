---
title: Important information and considerations when upgrading to Business Central
description: This article provides tips and considerations to prepare a solution when you're planning to upgrade to Business Central 2025 release wave 1 and later.
author: jswymer
ms.custom: bap-template
ms.topic: conceptual
ms.date: 04/07/2025
ms.author: jswymer
ms.reviewer: jswymer
---
# Important information and considerations when upgrading to Business Central

This article provides important information and tips for things to consider when you prepare to upgrade to [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2025 release 1 (version 26) The information that's relevant for you depends on which version you're upgrading from, and how much your solution differs from the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] base application.

## <a name="online"></a>Migrate to Business Central online

You can upgrade to [!INCLUDE[prod_short](../developer/includes/prod_short.md)] online from supported versions of [!INCLUDE[prod_short](../developer/includes/prod_short.md)] on-premises, as long as extensions handle your application customizations.

The process consists of two parts:

- Convert nonstandard functionality and customizations to apps and per-tenant extensions. Learn more in [Deploying a Tenant Customization](../developer/devenv-deploy-tenant-customization.md).
- Run the cloud migration tool, and then switch to use [!INCLUDE[prod_short](../developer/includes/prod_short.md)] online going forward. Learn more [Migrate on-premises data to Business Central online](../administration/migrate-data.md).

## New and changed application and platform features

There are several new and changed application features available in version 26 for users, administrators, and developers. For an overview of these features, consult:

- [What's new and planned for Business Central 2025 release wave 1](/dynamics365/release-plan/2025wave1/smb/dynamics365-business-central/planned-features)

## Deprecated or redesigned functionality

[!INCLUDE[prod_short](../developer/includes/prod_short.md)] occasionally deprecates features in application and platform. In most cases, features are replaced by more modern and sustainable features. If you're upgrading a solution that depends on the deprecated or changes functionality, you might have to change application code as part of the upgrade process. 

For example, sometimes code is refactored so that fields are no longer used. Or the functionality is moved from the base application to an extension. Typically, if you have custom extension code that depends on these fields, you have to create a new version of the extension to handle the change.

Learn more about the deprecated features in:

- [Deprecated Features in Application](deprecated-features-w1.md)
- [Deprecated Features in the Platform - Clients, Server, and Database](deprecated-features-platform.md)
- [Deprecated Fields, and Fields Marked as Obsolete](deprecated-fields.md)
- [Deleted objects in 2025 release wave 1](deleted-objects-25w1.md)

## Schema changes in subscription billing extension

Version 25.0 introduced the **Subscription & Recurring Billing** extension. In version 26, the extension is renamed to **Subscription Billing**. Several tables and fields in the extension are renamed, causing breaking changes when upgrading the extension from version 25.0 to 26.0 or later.

To upgrade the extension, you must synchronize the extension's database schema with the tenant database schema using a force sync operation. Force sync can cause data loss if custom code depends on the renamed tables and fields in the extension. To avoid data loss, refactor the custom code to match the extension's latest database schema before upgrading. For a list of renamed tables and fields, see [Renamed tables and fields](known-issues.md#renamed-tables-and-fields-in-susbscription-billing-extension-cause-synch-errors-on-upgrade).

## Important deployment-related changes

This section includes important changes that you need to consider when upgrading from version 22 and earlier to version 26.0. These changes were introduced in version 23.0.

- The default port for client services port for [!INCLUDE[server](../developer/includes/server.md)] changed to 7085 instead of 7046. You can still use 7046, but you have to change the port number in the [!INCLUDE[server](../developer/includes/server.md)] instance configuration. Learn more in [Configuring Business Central Server](../administration/configure-server-instance.md).
- NET Core no longer supports Server principle names (SPN). This change affects the delegation from the [!INCLUDE[webserver](../developer/includes/webserver.md)] to the [!INCLUDE[server](../developer/includes/server.md)] when they're on different computers.

  The affected scenarios are described in [Deploying Business Central in a Two-Computer Topology](../deployment/deploy-two-computer-environment.md) and [Deploying Business Central in a Three-Computer Topology](../deployment/deploy-three-computer-environment.md).

  Learn more about setting up delegation in [Configuring Delegation for Business Central Web Server](../deployment/configure-delegation-web-server.md). You can do this task anytime, but after upgrade, users won't be able to sign in to the web client until you do.

## Permissions and permission sets

[!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2021 release wave 1 (v18) introduced a new model for permissions. In previous versions, permission sets and permissions are defined only as data, which means they're stored in the tables of the application and tenant databases. Permission sets and permissions can now be defined in AL code as objects and packaged in extensions. This new model is the recommended model. Learn more in [Entitlements and Permissions](../developer/devenv-entitlements-and-permissionsets-overview.md).

- If you've already made the transition to the new permissions model in your current solution, then there's no extra work related to permission sets required for upgrade.
- If you're upgrading a solution that hasn't transitioned to the new permissions model, we recommend that you do. However, you can continue using the legacy model. Whichever model you choose, there's permission-related tasks you have to complete as part of upgrade. Learn more in [Upgrading Permissions Sets and Permissions](upgrade-permissions.md)

## Report platform

Version 20 introduced a new report rendering model. Previously, report rendering was done by the application. Now, by default, report rendering is done by the platform. In support of this new model, various changes have been made that affect upgrade from version 19 and earlier. If you're upgrading from version 20 or later, the solution already includes the necessary changes.

Learn more in [Upgrading reports](upgrade-reports.md).


## Related information  

[Upgrading the Application Code](Upgrading-the-Application-Code.md)  
[Upgrading the Data](Upgrading-the-Data.md)  
[Deprecated Fields, and Fields Marked as Obsolete](deprecated-fields.md)  
