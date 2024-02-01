---
title: "Update 17.1 for Microsoft Dynamics 365 Business Central 2020 Release Wave 2"
description: Get an overview of new and changed capabilities in the 17.1 update of Business Central online, which is part of 2020 release wave 2.
ms.author: solsen
ms.custom: na
ms.date: 04/01/2021
ms.reviewer: solsen
ms.topic: conceptual
author: EmmaNielsson
---

# Update 17.1 for Microsoft Dynamics 365 Business Central online 2020 release wave 2

Would you like to know what has changed in update 17.1? Below you'll find an overview and relevant links to what has been done on hotfixes and regulatory features in this update. In addition, we have gathered some good to know information and links, you might find interesting.

## Hotfixes

Find an overview of hotfixes in this [article](https://support.microsoft.com/help/4583515/update-17-1-for-microsoft-dynamics-365-business-central-2020-release-w).

## Feature changes

- [Enhanced email capabilities](/dynamics365-release-plan/2020wave2/smb/dynamics365-business-central/enhanced-email-capabilities)
- [Notify users of high-risk changes in selected setup fields](/dynamics365-release-plan/2020wave2/smb/dynamics365-business-central/notify-users-high-risk-changes-selected-setup-fields)
- [Use new sales pricing experience](/dynamics365-release-plan/2020wave2/smb/dynamics365-business-central/use-new-sales-pricing-experience-)
- [Control how Account Schedules for core financial reports are generated](/dynamics365-release-plan/2020wave2/smb/dynamics365-business-central/control-how-account-schedules-core-financial-reports-are-generated)
- [Improved VAT Registration no. lookup](/dynamics365-release-plan/2020wave2/smb/dynamics365-business-central/improved-vat-registration-no-validation)
- [Extension lifecycle telemetry in Application Insights for ISVs](../administration/telemetry-extension-lifecycle-trace.md)
- [Use environmentType and environmentName launch.json properties instead of obsoleted sandboxName](../developer/devenv-json-launch-file.md)
- [Symbols can be downloaded with a snapshot initialize launch.json configuration, using above environment properties](../developer/devenv-snapshot-debugging.md#download-symbols-on-the-snapshot-debugger-endpoint)


## Release Plan

If you want to get a comprehensive overview of what's new and planned for Business Central online for the entire 2020 release wave 2 (release from October 2020 through March 2021), find the link to the release plan [here](/dynamics365-release-plan/2020wave2/smb/dynamics365-business-central/planned-features).


## Upgrade to 17.1

Please note that new customers will automatically get the latest builds of Business Central (17.1). If you are an existing partner/customer, you will receive an email notification as soon as your environment has been upgraded.

## Good to know

**NEW! Migrate directly from version 14, 15, and 16 to Business Central online**  
Business Central includes a cloud migration tool that administrators can use to migrate customer data from on-premises databases to Business Central online. Starting now, the Cloud Migration app also supports migration from the earlier on-premises versions of Business Central, with the latest cumulative update applied: Migrate directly from versions 14.x, 15.x, and 16.x to version 17.x. 
This helps customers reduce their costs of migrating to the Business Central cloud significantly, as they can skip upgrading their on-premises environments to the latest version of Business Central and just migrate the data, including all historical transactions. The Cloud Migration app now includes all the necessary data upgrade logic to convert the data from the previous versions to the data structure of 2020 release wave 2 (version 17.0). Learn more [here](../administration/migrate-business-central-on-premises.md).

**Database size when migrating from Business Central on-prem to online**  
We have increased the limit we apply to the database size from 30 Gb to 80 Gb when migrating from Business Central on-prem to Business Central online using the Cloud Migration tool. If you are looking at migrating a larger database, we recommend that you contact the support team and work with them to make sure that the migration is successful. Learn more [here](../administration/faq-migrate-data.md#are-there-any-limits-on-the-amount-or-type-of-data-that-can-be-migrated) and read about running the cloud migration tool [here](../administration/migrate-data.md).  

**Watch what's new sessions on demand**  
Watch the sessions from the Business Central Launch Event in October. Register and get access to 30+ sessions [here](https://aka.ms/MSDyn365BCLaunchEvent).

**Snapshot debugging**  
Snapshot debugging has now been enabled for sandbox environments. It will be enabled in production in a later minor. Learn more [here](../developer/devenv-snapshot-debugging.md).

**Apps are moving to office.com**  
The home for all your business applications across Dynamics 365 and Microsoft Power Platform is moving to office.com, where you'll find the Business Central tiles for production and sandbox environments. Learn more [here](/dynamics365-release-plan/2020wave2/smb/dynamics365-business-central/apps-are-moving-officecom).

**Easy access to production or sandbox environments from the mobile app**  
Users of mobile devices can now choose between their sandbox and production environments without the need to use the pre-crafted URL as before. Partners running their own apps based on Business Central can also let their users explore it from mobile devices. Learn more [here](/dynamics365-release-plan/2020wave2/smb/dynamics365-business-central/access-multiple-production-or-sandbox-environments-mobile-apps).

**Unblock multifactor authentication for mobile apps**  
We have updated core authentication components of the mobile app to support multifactor authentication. Enabling such flow in the user setting on your Microsoft 365 account and then using it on a mobile device (via an SMS code, authenticator app, or more) is now possible after updating the Business Central mobile app to version 3.0 or higher. Learn more [here](/dynamics365-release-plan/2020wave2/smb/dynamics365-business-central/unblock-multi-factor-authentication-mobile-apps).