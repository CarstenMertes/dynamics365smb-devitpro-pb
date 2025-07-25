---
title: Update 25.3 for Microsoft Dynamics 365 Business Central 2024 release wave 2
description: Get an overview of new and changed capabilities in the 25.3 update of Business Central online, which is part of 2024 release wave 2.
ms.author: jswymer
ms.date: 01/27/2025
ms.update-cycle: 1095-days
ms.reviewer: jswymer
ms.topic: article
author: jswymer
ms.custom: 
    - bap-template
    - evergreen
---

# Update 25.3 for Microsoft Dynamics 365 Business Central online 2024 release wave 2

Would you like to know what changes are in update 25.3? Below you find an overview and relevant links to what was done on hotfixes and regulatory features in this update. In addition, we gathered some good to know information and links that you might find interesting.

## Hotfixes

Learn about the hotfixes and download on-premises files from Microsoft Support at [Update 25.3 for Business Central 2024 release wave 2](https://support.microsoft.com/help/5050249).

## Feature changes

- Chat with Copilot in more countries and regions

  We've expanded the public preview to more countries and regions, including: Albania, Andorra, Armenia, Austria, Belgium, Bosnia & Herzegovina, Bulgaria, Croatia, Cyprus, Czechia, Denmark, Estonia, Faroe Islands (Denmark), Finland, Georgia, Gibraltar, Greece, Greenland (Denmark), Hungary, Iceland, Ireland, Italy, Jamaica, Kazakhstan, Kosovo, Latvia, Liechtenstein, Lithuania, Luxembourg, Malta, Mexico, Moldova, Montenegro, Netherlands, North Macedonia, Poland, Portugal, Romania, San Marino, Serbia, Slovakia, Slovenia, Spain, Sweden, Switzerland, Ukraine, United States, and Vatican City.

  This feature is supported in English. While it can be used in other languages, it might not function as intended. Language quality might vary based on the user's interaction or system settings, which might impact accuracy and the user experience.

  Learn more in [Chat with Copilot](/dynamics365/business-central/chat-with-copilot) and check geographic and language availability at [Copilot international availability](https://aka.ms/bapcopilot-intl-report-external).

- Improvements to the **Copilot & AI capabilities** page

  The page now displays revised instructions and a link to the article [Azure OpenAI Service and Business Central data](https://go.microsoft.com/fwlink/?linkid=2298232) where administrators can learn about what data is processed by the Azure OpenAI Service. The article also provides transparency to EU customers, indicating that their data never leaves the EU Data Boundary.

- Improved security for Outlook add-in

  As part of our continual efforts to harden security of our online services, the Outlook add-in is silently switching to Nested App Authentication (NAA). For Business Central online, no action is required from admins or end-users. For on-premises, admins must update the setup to ensure the add-in works after February 1, 2025. Learn more in  [Modify existing Outlook add-in setup to support Nested App Authentication (NAA)](../administration/outlook-addins-setup-naa-modification.md).

## Localization updates

No localization updates for 25.3

## Release plan

Do you want to get a comprehensive overview of what's new and planned for Business Central online for the entire 2024 release wave 2 (release from October 2024 through March 2025)? Learn more at [Plan and prepare for Dynamics 365 Business Central in 2024 release wave 2](/dynamics365/release-plan/2024wave2/smb/dynamics365-business-central/)<!--(https://aka.ms/BCReleasePlan)-->.

## Upgrade to 25.3

New customers automatically get the latest builds of Business Central (25.3). If you're an existing partner/customer, you receive an email notification as soon as your environment is upgraded.

## Good to know

### Configuration packages for setup and evaluation data

We changed the way we prepare databases for new evaluation and production companies. Instead of using configuration packages to add demo and setup data, you now use the Contoso Coffee demo data app.

We shipped the Contoso Coffee demo data app in an earlier release to cover gaps in our demo and setup data, such as Manufacturing, Service, and Warehouse. Because the app is easy to use and now provides the comprehensive setup and demo data that was previously available in configuration packages, we're removing the configuration packages earlier available from the **Configuration Packages** page.

Starting with 25.3, when you launch the **Create New Company** assisted setup guide to initialize new companies with data, it checks whether Contoso Coffee demo data is installed and then displays a page that allows you to select specific demo and setup data.

![Shows the Create New Compay page in Business Central](../media/CreateNewCompanies.png)

#### For environment admins

In addition to making it easier to install rich demo data, this change also enables another improvement: flexible update policies for major and minor updates. Administrators now have extended update periods on environments. For major updates, there's a five-month period to test and prepare. For example, partners can spread out the workload of updating customer environments, and developers can verify app compatibility. Administrators can also opt out of minor updates during a grace period. Learn more at [Manage environment updates more flexibly](/dynamics365/release-plan/2024wave2/smb/dynamics365-business-central/manage-environment-updates-more-flexibly).

#### For developers

These changes might affect your extensions because we changed the logic of the **Create New Company** assist setup guide. Learn more in [Deprecated Features in the Base App: Configuration packages for setup and evaluation data](../upgrade/deprecated-features-w1.md#configuration-packages-for-setup-and-evaluation-data).

We continue to generate configuration packages for container and on-premises distribution media because some partners use them to run tests for their apps. This capability is a temporary solution to give partners time to switch to demo data generated by the Contoso Coffee Demo data app. It also allows partners to ensure that the tests are data agnostic and can generate needed data on the fly using available test libraries.

### Sales Order Agent in Business Central - Early Access Program (US only)

We recently announced the [Early Access Program for the Business Central Sales Order Agent](https://www.yammer.com/dynamicsnavdev/#/Threads/show?threadId=3092919011729408&search_origin=global&scoring=linear1Y-prankie-group-private-higher&match=any-exact&search_sort=relevance&page=1&search=sales%20order%20agent)&mdash;the first AI agent in Business Central, built to automate the entire sales requests capturing process. Spaces are limited, so sign up here: [https://aka.ms/bcAgentsEarlyAccess](https://aka.ms/bcAgentsEarlyAccess) (US region only at this time).

Learn more about the Sales Order Agent at [Use Copilot with agent capabilities to automate sales order-taking](/dynamics365/release-plan/2024wave2/smb/dynamics365-business-central/use-copilot-agent-capabilities-automate-sales-order-taking-process).

### New installation path started in 25.2

25.2 included internal database schema changes with the following consequences:

- New platform version 25.2 instead of 25.0.
- Different installation path than 25.0 and 25.1. Instead of using folder '250', components are installed in folder '252', for example: `C:\Program Files\Microsoft Dynamics 365 Business Central\252`.

Update 25.3 and future updates will also use platform number '25.2' and installation folder '252'.

### Business Central Launch Event videos on YouTube

The Business Central Launch Event for the 2024 release wave 2 took place on October 18, 2024. This online event aimed to provide information about the new features and enhancements in the 2024 release wave 2 to resellers, partners, ISVs, and consultants. You can find over 40 videos of this event on YouTube by visiting [aka.ms/BCLE](https://aka.ms/BCLE).

### Features becoming mandatory soon

Prepare for features becoming mandatory soon. Learn more in [Optional features that are now mandatory](https://aka.ms/BCFeatureMgmt).

When the following features become mandatory, they might have potentially disruptive effects on extensions and apps you install in the future. These features are now optional to use and can be enabled in the **Feature Management** page in Business Central. Learn in more [Enabling Upcoming Features Ahead of Time](../administration/feature-management.md)).

- **Extending G/L Entry Aggregations When Posting Invoices**

   This feature is generally available with Update 23.1 and becoming mandatory in Update 26.0 (2025 release wave 1). The Invoice Posting interface replaces the use of the **Invoice Post. Buffer** table. The replacement helps resolve extensibility issues for the legacy Invoice Post. Buffer table. You can now use your own implementation of G/L invoice posting. As a developer, you can learn more about how to extend G/L entry aggregations when posting invoices [Extending G/L Entry Aggregations When Posting Invoices](../developer/devenv-invoice-posting-example.md).

- **New extensible exchange rate adjustment**

   This feature, including the posting review feature, is generally available with Update 23.0 and becoming mandatory in Update 26.0 (2025 release wave 1). New capability replaces the legacy Exchange Rates Adjustment Report. This new capability increases extensibility and makes it easier to comply with local and industry-specific requirements. It also gives you more control over exchange rate adjustments with a posting preview and how dimension values are post when you adjust exchange rate, and better reporting. As a developer, you can learn more about how to extend G/L entry aggregations when posting invoices in [Extending Currency Exchange Rate Adjustments](../developer/devenv-extend-exchange-rates.md).

Before the features become mandatory, work with your partner to update installed extensions and apps.

### Discover all partner related resources

Are you a partner who wants a list of relevant resources? Learn more in [Resources for Partners](https://aka.ms/BCAll).

### Discover all user related resources

Are you a user who wants a list of relevant resources? Learn more in [Resources for users](https://aka.ms/BCUsers).  
