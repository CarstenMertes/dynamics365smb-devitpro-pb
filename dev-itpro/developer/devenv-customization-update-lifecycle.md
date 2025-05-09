---
title: "Update Lifecycle for Tenant Customizations"
description: "Overview of the process of ensuring extension compatibility with update versions"
author: jaredha

ms.topic: reference
ms.author: jaredha
ms.date: 04/01/2021
ms.reviewer: jswymer
---

# Update Lifecycle for Customizations of [!INCLUDE[prod_short](../developer/includes/prod_short.md)] Online

When you create a tenant-specific customization, or an extension that is scoped to a single [!INCLUDE[prod_short](../developer/includes/prod_short.md)] environment (often referred to as per-tenant extensions), you must take the lifecycle of the extension into consideration. For more information about the extension lifecycle and events that can cause incompatibilities between the extension and base application, see [The Lifecycle of Apps and Extensions for Business Central](devenv-app-life-cycle.md). 

You are responsible for your extension. You own the process of updating the extension and providing upgrade code if the schema changes between versions of the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] base application. When an update is available for your [!INCLUDE[prod_short](../developer/includes/prod_short.md)] environment, all extensions, both AppSource extensions and tenant customizations, must be compatible with the next version of the base application before the update can be installed on the environment. You are responsible for ensuring that your extensions are compatible with the update version.

In this article, we describe the process for ensuring update compatibility for tenant customizations.

## Automated Extension Validation

An automated service validates all tenant customizations before an update is marked for a scheduled update of an environment. This validation compares the extension's dependencies with the updated version of the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] application to see if any changes caused incompatibilities with the new version.

If the validation service discovers any tenant customizations that are not compatible with the update, an email notification is sent to the tenant administrators listed on the **Notification recipients** tab of the [!INCLUDE[prodadmincenter](../developer/includes/prodadmincenter.md)]. For more information, see [Managing Tenant Notifications](../administration/tenant-admin-center-notifications.md).

> [!IMPORTANT]
> At least one email address must be specified as a notification recipient to receive the update notifications. If you do not specify an email address, you will not be notified of updates and other changes to the tenant.

The email notification provides information on the incompatible extension, detail on which properties must be updated, and steps to bring the extension into compatibility.

## Update Failure Notification

If a [!INCLUDE[prod_short](../developer/includes/prod_short.md)] environment has an extension that is not compatible with the update version, the update cannot be applied. If an update fails due to an incompatible extension, a notification is sent to the tenant administrators listed on the **Notification recipients** tab of the [!INCLUDE[prodadmincenter](../developer/includes/prodadmincenter.md)].  

The notification is similar to that provided by the automated extension validation. It provides information on the incompatible extension, detail on which properties must be updated, and steps to bring the extension into compatibility.

## Automatic Extension Removal

The publisher of an extension must maintain compatibility with the new release of [!INCLUDE[prod_short](../developer/includes/prod_short.md)]. For more information about automatic removal of incompatible extensions, see [Maintain AppSource apps and PTEs in Business Central online](app-maintain.md).

## Related information

[Retaining table data after publishing](devenv-retaining-data-after-publishing.md)  
[Upgrading Extensions](devenv-upgrading-extensions.md)  
[Updating Environments](../administration/tenant-admin-center-update-management.md)  

