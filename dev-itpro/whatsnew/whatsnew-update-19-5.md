---
title: "Update 19.5 for Microsoft Dynamics 365 Business Central 2021 Release Wave 2"
description: Get an overview of new and changed capabilities in the 19.5 update of Business Central online, which is part of 2021 release wave 2.
ms.date: 04/01/2024
ms.update-cycle: 1095-days
ms.reviewer: solsen
ms.topic: article
author: SusanneWindfeldPedersen
ms.custom: evergreen
---

# Update 19.5 for Microsoft Dynamics 365 Business Central online 2021 release wave 2

Would you like to know what has changed in update 19.5? Below you'll find an overview and relevant links to what has been done on hotfixes and regulatory features in this update. In addition, we have gathered some good to know information and links, you might find interesting.

## Hotfixes
Find an overview of hotfixes in this [article](https://support.microsoft.com/en-us/topic/update-19-5-for-microsoft-dynamics-365-business-central-on-premises-2021-release-wave-2-application-build-19-5-36700-platform-build-19-0-36625-c9b94708-c269-4b64-a288-1d7c7c50f919).

## Localization updates

| Country| Feature  |Description|
|-------------|--------------|--------------|
|Norway | Updated SAF-T export | Fixed issue with exporting bank data in SAF-T in accordance with BankAccountStructure |
| India | Preview Posting on Service Transfer Order | Document Service Transfer Order in the Indian localization now has Preview Posting action to enable review of the different types of entries that will be created when you post the document. |

## Release Plan  
If you want to get a comprehensive overview of what's new and planned for Business Central online for the entire 2021 release wave 2 (release from October 2021 through March 2022), find the link to the release plan [here](/dynamics365-release-plan/2021wave2/smb/dynamics365-business-central/planned-features).

## Upgrade to 19.5

Please note that new customers will automatically get the latest builds of Business Central (19.5). If you are an existing partner/customer, you will receive an email notification as soon as your environment has been upgraded.

## Good to know

**Discover the features for 2022 release wave 1**  
Discover what's new and planned for Dynamics 365 Business Central 2022 release wave 1. You can find the list of features here: [aka.ms/BCReleasePlan](https://aka.ms/BCReleasePlan).

**Avoid an unexpected data upgrade during cloud migration**  
When you run cloud migration from a previous version of Business Central, one of the process steps is to run the data upgrade logic to align the migrated data to the format of the current version. We strongly recommend that you perform this step one time after you have completed the migration of all your customer’s data to the online environment. If a planned Business Central major or minor update is applied to this environment, the update will automatically include the upgrade of the data that was migrated by the cloud migration. These planned updates also turn off cloud migration for the environment. To avoid this situation, and to allow you to complete the migration and data upgrade for your environment, we recommend that you postpone any scheduled major and minor updates for the target environment until you have completed cloud migration. You can postpone updates in the Business Central admin center. For more information, see [Managing Updates](/dynamics365/business-central/dev-itpro/administration/tenant-admin-center-update-management).  

**Upcoming Business Central Office Hours Calls**  
Make sure to join the office hours call 'Business Central apps in AppSource' on March 8. The call is at 5.00pm - 6.00pm CET / 08.00am -09.00am PST. Register and stay tuned for upcoming calls: [aka.ms/BCOfficeHours](https://aka.ms/BCOfficeHours). Watch on-demand recordings: [aka.ms/BCOfficeHoursRecordings](https://aka.ms/BCOfficeHoursRecordings).  

**Action needed: Client secret-based service to service authentication deprecation for Microsoft hosted tenants integrating to Dataverse**  
To ensure no disruptions in integration between Business Central and Dataverse you must upgrade your Business Central connection to Dataverse to certificate-based authentication.  
The change will happen in March 2022. We strongly recommend you perform steps outlined in [Upgrade Connections from Business Central Online to Use Certificate-Based Authentication](/dynamics365/business-central/admin-how-to-set-up-a-dynamics-crm-connection#upgrade-connections-from-business-central-online-to-use-certificate-based-authentication) as soon as possible.

**Join Directions NA on April 3-6, 2022**  

Directions North America is a Microsoft Dynamics 365 event driven by Partners – for Partners. Attendees will build new business contacts, learn about best practices, and discover valuable tools for execution and success. Attendees can also use the many networking opportunities at the conference to grow and enhance relationships with other partners, ISVs, service providers, and Microsoft. Learn more and register [here](https://www.eventsquid.com/event.cfm?event_id=14536). 
