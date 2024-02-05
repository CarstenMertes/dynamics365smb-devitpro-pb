---
title: "Update 21.5 for Microsoft Dynamics 365 Business Central 2022 Release Wave 2"
description: Get an overview of new and changed capabilities in the 21.5 update of Business Central online, which is part of 2022 release wave 2.
ms.author: a-enielsson
ms.custom: na
ms.date: 03/06/2023
ms.reviewer: jswymer
ms.topic: conceptual
author: EmmaNielsson
---

# Update 21.5 for Microsoft Dynamics 365 Business Central online 2022 release wave 2

Would you like to know what has changed in update 21.5? Below you'll find an overview and relevant links to what has been done on hotfixes and regulatory features in this update. In addition, we have gathered some good to know information and links, you might find interesting.

## Hotfixes

Find an overview of hotfixes in this [article](https://support.microsoft.com/help/5024403) and the downloads [here](https://aka.ms/BCDownload).

## Feature changes  
- [Copying the SystemID and data audit fields using CopyRows](/dynamics365/business-central/dev-itpro/developer/devenv-data-transfer#copy-rows)

## Localization updates

| Country/region | Feature  |Description|
|-------------|--------------|--------------|
| All countries/region | Added field Registration No. to Customers and Vendors | Business Central previously had a Registration No. field in the Company Information, but no such field in Customer or Vendor cards. In some localizations, this field already existed, so now this fields are delocalized and you can use them in global version
| Belgium | Deferrals on local Purchase/Sales Ledger reports | Business Central posts the deferral entries in the same journal as the original invoice or credit memo. This model previously made problems when print out the purchase ledger, and sales ledger (BE local reports). Both the purchase ledger and the sales ledger now show the invoices, and credit memos without deferrals.|
| Belgium | Intervat VAT declaration version 9 | Intervat VAT declaration has been updated against the newest required version - v0.9. It is now already possible to add the comment into the Intervat VAT XML file in order to inform the VAT administration. |
| United States | Added EIN Number and IRS Employee Contact | The EIN Number and IRS Employee Contact (referenced with Employees) has been added to the Company Information. Also, when users prints IRS 1096 report, these two fields will be populated by default. |

## Release Plan

If you want to get a comprehensive overview of what's new and planned for Business Central online for the entire 2022 release wave 2 (release from October 2022 through March 2023), find the link to the release plan [here](/dynamics365-release-plan/2022wave2/smb/dynamics365-business-central/planned-features).

## Upgrade to 21.5

Please note that new customers will automatically get the latest builds of Business Central (21.5). If you are an existing partner/customer, you will receive an email notification as soon as your environment has been upgraded.

## Good to know

**Business Central 2023 release wave 1 is coming. Register for the free, digital Business Central Launch Event, March 29-31**  
Join us again this year when we're hosting the Business Central Launch Event. We're kicking off the event with a live opening session, followed by access to 28 what's new sessions, and live Q&As. Register now: [aka.ms/BCLE](https://aka.ms/BCLE).   

**Public preview for Business Central 2023 release wave 1 is live**  
Partners can try out new functionality in preview environments. Use Microsoft Collaborate to submit your feedback or to report any potential issues that you discover in the preview, discover how: [aka.ms/BCPreview](https://aka.ms/BCPreview). Join the Yammer group to share feedback directly with Microsoft product team or ask questions related to the preview [here](https://www.yammer.com/dynamicsnavdev/#/threads/inGroup?type=in_group&feedId=128509960192&view=all).

**Join us for updates on LinkedIn!**  
Follow the new company page for Microsoft Dynamics 365 Business Central on LinkedIn. We’ll share updates, announcements, and other “good to know” stuff. Join us [here](https://www.linkedin.com/company/microsoft-dynamics-365-business-central/). 

**Upcoming Business Central Office Hours Calls**  
In March, we will be hosting the following call, which you can already register for today:

- **March 14:** Onboarding your customers to Business Central

Register and stay tuned for upcoming calls: [aka.ms/BCOfficeHours](https://aka.ms/BCOfficeHours). Watch on-demand recordings: [aka.ms/BCOfficeHoursRecordings](https://aka.ms/BCOfficeHoursRecordings). 

**Discover resources on aka.ms/BCAll**  
Are you looking for relevant resources? Find it all in this article [aka.ms/BCAll](https://aka.ms/BCAll) and remember to bookmark it!
