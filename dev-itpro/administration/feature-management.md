---
title: Enabling upcoming features ahead of time
description: Learn how to enable select features ahead of time as the administrator of Business Central online or on-premises. 
author: mikebcMSFT

ms.topic: conceptual
ms.reviewer: na
ms.search.keywords: administration, tenant, admin, environment, key, optional, feature management, early access, preview, what's new
ms.date: 10/26/2021
ms.author: mikebc
---

# Enabling Upcoming Features Ahead of Time

We add new capabilities to [!INCLUDE [prod_short](../includes/prod_short.md)] in major updates and minor updates. Some new features can be enabled ahead of time on sandbox and production environments. Learn how you as an administrator can turn on new features using the **Feature Management** page.

## Managing optional features

Some new features can be enabled ahead of time on sandbox and production environments. This capability allows you to benefit as early as possible from feature improvements and innovative new features. It gives you the time you need to test and prepare your organization for change.

When Microsoft releases features or feature design improvements as part of minor updates, some features aren't immediately enabled. Users as well as administrators can learn about these features in the release plans, and administrators can enable each individual feature from the **Feature Management** page inside [!INCLUDE [prod_short](../includes/prod_short.md)]. Once a feature is enabled, it becomes available for all users on that environment no matter how they access [!INCLUDE[prod_short](../includes/prod_short.md)].  

These features are only optional for a while. The option period typically starts from the minor update in which they're made generally available. The period ends when the features become mandatory and are automatically enabled in a later major update. To see the approximate date and service update when each feature is expected to become mandatory, see the **Automatically enabled from** field in the **Feature Management** page. After this date, the feature will no longer appear in the **Feature Management** page and can no longer be turned off. To learn more about features that are now, or soon will be mandatory or generally available, go to [Optional Features that are Now Mandatory](feature-management-mandatory-features.md).  

> [!IMPORTANT]
> The projected timeline for a feature is subject to change (see [Microsoft policy](https://go.microsoft.com/fwlink/p/?linkid=2007332)).

### Example timeline for an optional feature

> [!div class="mx-imgBorder"]
> ![Example timeline for an optional feature.](../media/timeline-optional-features.png "An example timeline for an optional feature in the Feature Management page")

Learn about [what's new and planned](/dynamics365-release-plan/2021wave1/).  
Learn about [new features available in the last minor update in a release wave](../whatsnew/whatsnew-update-17-5.md).  

> [!TIP]
> To prepare for an upcoming feature, consider enabling the feature on a sandbox environment that has a copy of production data. Invite business users to test out the change using real-world tasks. Once you and your users are satisfied with the change, you can then enable it on production environments where they can immediately benefit from that feature.

## How to enable an optional feature

> [!NOTE]
> Features might require that one or more other features are also enabled, and perhaps even first. If the feature you want to turn on depends on other features, [!INCLUDE[prod_short](../includes/prod_short.md)] will let you know. The prerequisite features are indented beneath the feature you want to turn on. Information about prerequisites is also available in the **Dependent Features** FactBox.

1. Sign in to your environment and navigate to the **Feature Management** page, or use this link: [https://businesscentral.dynamics.com/?page=2610](https://businesscentral.dynamics.com/?page=2610).
2. If the page isn't editable, choose the **Edit List** action.
3. For the feature you want to turn on, in the **Enabled for** field, choose **All users**.

As soon as you enable the feature, any user who signs in to that environment experiences the change. You won't necessarily experience the change yourself until you sign out and sign in again, or start a new session.

> [!TIP]
> Try out the feature for yourself without enabling it for all users by choosing the **Try it out** link. This will open a new browser tab with the feature enabled for that session. Any new sessions in your browser will also have the feature temporarily turned on. To stop trying the feature, close your browser window or sign out.  

If you manage multiple environments, such as several sandboxes, new features can be enabled in some of these environments and not in other environments. It can be tricky to keep track of what is enabled where in such scenarios, but the **Feature Management** page always shows what is enabled in a given environment.

## Features that can't be turned off

Some features or feature improvements may permanently affect the state and capabilities of [!INCLUDE[prod_short](../includes/prod_short.md)] and can't be safely reverted. These irreversible features can't be turned off again after they've been enabled. Before you turn on an irreversible feature on a production environment, we recommend that you first evaluate it in a sandbox environment that is a copy of the production environment.  

> [!NOTE]
> When you choose to enable an irreversible feature, a warning dialog that describes the consequences is displayed. Choose the **Yes** action to turn on the feature in that environment.

Starting with version 19.1, when you create a copy of an environment, any irreversible features that were turned on are also available in the copy.  

## Scheduling data updates for new features

Enabling application features that change the user experience or update data can be a disruptive process. So you might want to go at your own pace. For example, schedule an update per company for a time that's after your users have been trained for the new experiences.  

You schedule a data update on the **Feature Management** page by choosing the **Schedule** action, or by choosing **All Users** in the **Enable for** column. Both of those actions start the **Feature Data Update** setup guide. This guide allows you to review the affected data and schedule the update process. When the data update process is completed, the feature is enabled in the company where you ran the data update.

> [!NOTE]
> For a feature that requires data update, data is created based on the data for the existing feature. The data for the existing feature may remain available, however, it is not synchronized with data for the new feature. Therefore, we recommend that you use one feature or the other, but not both.

## <a name="permission"></a>Control user access to feature management

Most users, by default, won't have permission to enable upcoming features themselves. As an administrator, the easiest way to give a user permission is to assign them the **FEATURE MGT. - ADMIN** permission set. For more information, see [Assigning Permission Sets](/dynamics365/business-central/ui-define-granular-permissions). This permission set was introduced in version 18.1.

## FAQ about Feature Management

### Why do I have to enable another feature before I can get the feature I want?

Some features are built to work together with one or more other features. That means that a feature might need functionality that another feature provides, so you must enable the other features first. When that's the case, the dependent features are indented under the primary feature in the list.  

### There are no features listed as optional. Did I do something wrong?

There may be periods where no optional features have been made available, which is perfectly normal. There will likely be few or no features listed in the **Feature Management** page immediately after a major update.

#### Why can't I enable features and make other changes on the Feature Management page?

Chances are you don't have permissions to this page. See [Control user access to feature management](#permission) or talk to an administrator.

#### Will all new features eventually be listed on the Feature Management list?

No. We carefully select applicable features based on different criteria so that only a manageable subset of new features will appear in the list. Selected features are primarily those features that change the visuals or behaviors of the user interface and which require significant effort for business users to adjust to.

### Are these features still under development or in beta/preview?

No. Features listed in the Feature Management page are considered ready and generally available. Most of these features are automatically enabled on newly provisioned environments for new customers to benefit from.

### Does Microsoft provide support for optional features?

Yes. Features that are listed in the **Feature Management** page are considered ready. They follow the standard support lifecycle for the service update in which they're first made available.

### Will Business Central notify me closer to the date when a feature becomes mandatory?

No. Users and administrators don't receive any in-app or email notifications about approaching dates for features becoming automatically enabled.  

### Do these features show in the Microsoft 365 admin center Message center?

At this time, new [!INCLUDE[prod_short](../includes/prod_short.md)] features aren't listed in Message center.  

### How is feature management different to the Early Access program?

The Early Access program that is used by some Dynamics 365 apps makes a large set of new features available two months before a major update. It allows customers to enable those features in production. The most significant difference is that the Early Access program features are always two months before the major update.

### How is feature management different to preview environments?

Preview environments are [!INCLUDE[prod_short](../includes/prod_short.md)] online sandbox environments that include all new platform and application features that will become available with the upcoming major update. The most significant difference is that a preview environment includes all new features bundled together. You don't have the opportunity to select which feature to enable and test.  

### How is feature management different from application area tags?

Application areas are a concept where developers specify differentiated user experiences in the business application. By using application areas, developers can show or hide individual controls on a page. Like feature management, application areas concept also puts administrators in control of selecting the preferred experience tier. One difference is that there's no time period during which application areas can be optionally enabled. Another difference is that they only apply to business application controls.  

### Can resellers, ISVs, and developers contribute to the list of features?

No. At this time, feature management is only for features that are released by Microsoft.

### Can I turn on a feature for a single user?

No. Business Central doesn't let you turn on a feature for a single user or group of users. Enabled features apply to all users of an environment.  

### I don't see a link to try out an optional feature. Is something wrong?  

Some features don't provide a way to try it out for yourself and won't display a **Try it out** link. Before you turn on these features, we recommend that you first test the features in a sandbox environment that is a copy of the production environment.

### Are optional features also optional on new environments?

Yes. Most optional features are turn on by default in new environments for new customers to benefit from. Administrators can still turn any of these features off from the **Feature Management** page. Some features are irreversible and aren't turn on by default.  

Starting with version 19.1, when you create a copy of an environment, any irreversible features that were turned on are also available in the copy.  

#### Are optional features automatically enabled on sandbox environments?

When you create a new sandbox environment with a copy of production data, your choice of enabled features is also copied to the sandbox. When you create a fresh sandbox, each feature is enabled by default, unless a feature is irreversible.  

### Why does the list include features that apply to other countries/regions?

Microsoft's business functionality in [!INCLUDE [prod_short](../includes/prod_short.md)] consists of functionality that is generic and functionality that is particular to a specific country or region. The **Feature Management** page will at times show optional features that are particular to a country, even if your [!INCLUDE [prod_short](../includes/prod_short.md)] is based on another country-specific version. This is due to the current limitations of feature management, which relies on a system table to populate the **Feature Management** page.  

In a future version, we hope to redesign feature management to better reflect local functionality and partner-provided functionality.  

### Is feature management applicable to on-premises deployments of Business Central?

Yes. You can turn optional features on or off in a similar way.

## See also

[New and planned features](/dynamics365-release-plan/2021wave1/)  
[Administration of [!INCLUDE[prod_short](../includes/prod_short.md)] Online](tenant-administration.md)  
[Major updates of [!INCLUDE[prod_short](../includes/prod_short.md)] Online](update-rollout-timeline.md)