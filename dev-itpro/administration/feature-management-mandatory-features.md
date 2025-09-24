---
title: Optional Features Now Mandatory
description: Learn about the features that were optional but are now mandatory.
author: brentholtorf
ms.author: bholtorf
ms.reviewer: bholtorf
ms.topic: article
ms.date: 06/19/2025
ms.update-cycle: 180-days
ms.custom: bap-template
ms.collection:
  - bap-ai-copilot
---

# Optional features that are now mandatory

This article provides the following information about optional features, starting with 2023 release wave 1:

* Features that are now mandatory and can't be disabled. Feature keys are removed from **Feature Management**.
* Features that are turned on by default for new customers
* Features that are now generally available

Some of the features or design improvements in major and minor updates are optional and aren't immediately enabled. You can learn about these features in the release plans and documentation and decide whether your administrator should turn them on. To learn more about optional features, go to [Enabling Upcoming Features Ahead of Time](feature-management.md).

However, these features are only optional for a while. The period in which they're optional typically starts when the update they're made in becomes generally available. The period ends when the features become mandatory and are automatically enabled. The approximate date and service update when we expect to make each optional feature mandatory is shown in the **Automatically enabled from** field on the **Feature Management** page. After that date, the feature will no longer appear on the Feature Management page, and you can't turn it off. To learn more about the optional period, go to [Example timeline for an optional feature](feature-management.md#example-timeline-for-an-optional-feature).

## 2025 release wave 2 (version 27)

### Features mandatory in version 27

These features are no longer controlled in **Feature management**, so they can't be disabled.

- [Feature Update: Enable multiple users to post warehouse entries at the same time](https://go.microsoft.com/fwlink/?linkid=2274007)
- [Feature Update: Enable use of package tracking in physical inventory orders](/dynamics365/business-central/inventory-how-work-item-tracking)
- [Feature Update: Enable using 1099 forms to transmit the tax data to the IRS in the United States](/dynamics365/business-central/localfunctionality/unitedstates/set-up-use-irs1099-form)
- [Feature: Add fields from related tables in analysis mode.](/dynamics365/business-central/analysis-mode-feature-key)
- [Feature: Enable server certificate validation for Http requests](/dynamics365/business-central/dev-itpro/developer/devenv-httpcertvalid-feature-key)
- [Feature: Optimize screen estate usage on the web](/dynamics365/release-plan/2025wave1/smb/dynamics365-business-central/optimize-screen-estate-usage-web)	

### Features added and enabled by default in version 27

- [Feature Update: Provides functionality for having default values for financial reports](/dynamics365/release-plan/2025wave2/smb/dynamics365-business-central/use-enhanced-financial-reporting)
- Feature: Introduce UI support for masking sensitive data.

### Features added and disabled  by default in version 27

- [Feature: Advanced Tell Me (preview)](https://go.microsoft.com/fwlink/?linkid=2331650)

## Existing features now enabled by default

- [Feature Update: Enable multiple users to post item ledger entries and value entries at the same time](https://go.microsoft.com/fwlink/?linkid=2299833) 
- [Feature Update: Enable multiple users to post job ledger entries at the same time](https://go.microsoft.com/fwlink/?linkid=2299833)  <!-- missing rp-->
- [Feature Update: Enable multiple users to post resource ledger entries at the same time entries at the same time](https://go.microsoft.com/fwlink/?linkid=2299833)  <!-- missing rp-->
- [Feature: Calculate only visible FlowFields](../developer/calculate-only-visible-flowfields-feature-key.md)

### Other feature key changes

- [Feature: Enables advanced navigation (not data) search capabilities by utilizing semantic similarity search on application metadata](../developer/semantic-search-feature-key.md) renamed to **Feature: Preview semantic similarity search on application metadata**.

## 2025 release wave 1 (version 26)

### Features mandatory in version 26

These features are no longer controlled in **Feature management**, so they can't be disabled.

- [Feature Update: Enable use of new extensible exchange rate adjustment, including posting review](https://go.microsoft.com/fwlink/?linkid=2187318)
- [Feature Update: Enable use of new extensible invoice posting engine](https://go.microsoft.com/fwlink/?linkid=2187318)
- [Feature Update: Replace the existing EU 3-Party Trade Purchase functionality with the new EU 3-Party Trade Purchase extension](https://go.microsoft.com/fwlink/?linkid=2235119) - Still applies to Sweden (SE) and Finland (FI) localized versions.
- [Feature: Enable legacy locking scheme in AL](https://go.microsoft.com/fwlink/?linkid=2244711)
- [Feature: Enable using bulk operations for Shopify connector](https://go.microsoft.com/fwlink/?linkid=2242514)

### Features added and enabled by default in version 26

- [Feature: Disable SOAP web services on Microsoft UI pages](../developer/devenv-disable-soap-microsoft-pages-feature-key.md)<!-- missing rp-->
- [Feature: Enable server certificate validation for HTTP requests](../developer/devenv-httpcertvalid-feature-key.md)

### Features added and disabled by default in version 26

- [Feature Update: Enable multiple users to post item ledger entries and value entries at the same time](https://go.microsoft.com/fwlink/?linkid=2299833) 
- [Feature Update: Enable multiple users to post job ledger entries at the same time](https://go.microsoft.com/fwlink/?linkid=2299833)  <!-- missing rp-->
- [Feature Update: Enable multiple users to post resource ledger entries at the same time entries at the same time](https://go.microsoft.com/fwlink/?linkid=2299833)  <!-- missing rp-->
- [Feature: Calculate only visible FlowFields](../developer/calculate-only-visible-flowfields-feature-key.md)
- [Feature: Enables advanced navigation (not data) search capabilities by utilizing semantic similarity search on application metadata](../developer/semantic-search-feature-key.md)<!-- missing rp-->
- [Feature Update: Convert the manufacturing flushing method 'Manual', so that it no longer requires picking.](https://go.microsoft.com/fwlink/?linkid=2303767)

## 2024 release wave 2 (version 25)

### Features mandatory in version 25

These features are no longer controlled in **Feature management**, so they can't be disabled.

* [Feature Update: Use new customer and item templates in Shopify instead of the generic templates](https://go.microsoft.com/fwlink/?linkid=2224515)
* [Feature: Convert user group permissions](https://go.microsoft.com/fwlink/?linkid=2220446)

### Features enabled by default in version 25

* [Feature Update: Enable multiple users to post warehouse entries at the same time](https://go.microsoft.com/fwlink/?linkid=2274007)
* [Feature: Use optimized text search in lists](/dynamics365/business-central/ui-enter-criteria-filters#choose-between-modern-search-and-legacy-search)

## 2024 release wave 1 (version 24)

### Features mandatory in version 24

These features are no longer controlled in **Feature management**, so they can't be disabled.

|Feature  |Description  |
|---------|---------|
|[Modern Action Bar](/dynamics365-release-plan/2022wave2/smb/dynamics365-business-central/modern-action-bar)|A promoted section of the action bar can help you learn the product, improve your productivity, and make the product easier to use. You can tailor it to fit the needs of your industry, company, or yourself. Add actions that you want to make available in an easily discoverable and consistent way across the product for new users to quickly learn the product, or tailor it to your business-specific needs for proficient users.|
|[New approval workflow experience with Power Automate templates](/dynamics365/release-plan/2023wave1/smb/dynamics365-business-central/new-approval-workflow-experience-templates-power-automate)|[!INCLUDE [prod_short](../developer/includes/prod_short.md)] online customers who use Power Automate to run document approval workflows are able to do so easily with this release. Several actions linked to workflow approvals and Power Automate have been improved with more support for selecting one of many templates for each document type. Users and decisions makers can use Power Automate to run approval and take advantage of the rich experience.|
|[Search for pages and data in the mobile app](/dynamics365/release-plan/2023wave2/smb/dynamics365-business-central/search-pages-data-mobile-app)|Adds the popular Tell Me experience to mobile devices that run the [!INCLUDE [prod_short](../developer/includes/prod_short.md)] app. It also provides access to the Tell Me built-in data search.|
|[Feature Update: Use tracking by package number in reservation and tracking system](/dynamics365-release-plan/2021wave1/smb/dynamics365-business-central/additional-dimensions-item-tracking-as-foundation-vertical-solutions)|Support for a third dimension for item tracking that you can use as is to keep track of simple warehouse management packages or pallets, or which you can use as a foundation for advanced vertical solutions.|
|[Feature Update: Replace the existing Automatic Account Codes functionality with the new Automatic Account Codes extension](/dynamics365/release-plan/2023wave1/smb/dynamics365-business-central/automatic-account-codes)|People who work with documents can save time by using automatic account codes to allocate recurring transactions in a faster way. You can use customized posting groups to automate recurring transactions in journals, sales documents, or purchase documents. These posting groups can be used throughout [!INCLUDE [prod_short](../developer/includes/prod_short.md)] to trigger automatic postings and allocations across different accounts or dimensions. |
|[Feature Preview: Bank account reconciliation with Copilot](/dynamics365/release-plan/2023wave2/smb/dynamics365-business-central/complete-bank-account-reconciliation-faster-copilot)|Bookkeepers in SMB organizations need to import bank statements and reconcile transactions with their bank ledger entries, making sure all transactions are accounted for. While [!INCLUDE [prod_short](../developer/includes/prod_short.md)] already reduces effort through rule-based transaction matching, the residual work to process the unmatched transactions every week remains cumbersome and quickly accrues to lost workdays. Copilot reduces bookkeeping effort by matching more transactions and suggesting G/L accounts to post the remaining transactions.|
|[Feature Update: Use the platform table 'Report Layout List' for adding and selecting layouts in the 'Report Selection' pages](/dynamics365/business-central/dev-itpro/developer/devenv-howto-report-layout?wt.mc_id=d365bc_inproduct_page)|When enabled, report selection and report layout selection are handled from the platform using data managed by extensions. This strategy lets [!INCLUDE [prod_short](../developer/includes/prod_short.md)] select layouts that were shipped with extensions or uploaded by users. The previous strategy used layout selection based on data in Custom Report Layout table, which didn't handle extension layouts.|
|[Feature: New Microsoft Word report rendering platform.](../developer/devenv-howto-report-layout.md)|Word-based document reports were rendered by an add-in in application code using the MergeDocument platform trigger. The document generation is now fully managed by the platform and the application code is marked as obsolete.|
|[Feature: Create AI-powered product descriptions with Copilot](/dynamics365/release-plan/2023wave2/smb/dynamics365-business-central/get-marketing-text-suggestions-copilot)|Business Central's first copilot feature, marketing text suggestions, moves from public preview to being generally available. This feature provides the following benefits:<br>* Start with a picture<br>* Author marketing copy<br>* Get AI-powered suggestions<br>* Customize suggestions<br>* Publish to Shopify|
|[Feature Update: Legacy list views are hidden](/dynamics365-release-plan/2022wave2/smb/dynamics365-business-central/legacy-list-views-are-hidden)|Legacy views are list views that were created by developers in previous versions of [!INCLUDE [prod_short](../developer/includes/prod_short.md)] by placing them on the Role Center page. [!INCLUDE [prod_short](../developer/includes/prod_short.md)] displays legacy views side by side with modern views directly on the list page, but legacy views offer a degraded experience and fewer options compared to modern views.|
|[Feature Update: Replace VAT Date CZ with VAT Reporting Date- Czechia](/dynamics365/release-plan/2023wave1/smb/dynamics365-business-central/replace-vat-date-cz-vat-reporting-date--czechia)|Some countries/regions require reporting for VAT statements and VAT returns by using a date that's different than the posting date. Sometimes, the date can be the document date, but even this date can differ from the requirement. For this reason, the VAT Date exists on all purchase and sales documents and on journals.|
|[Feature update: Enable using SIE Audit Files Exports](/dynamics365/business-central/localfunctionality/sweden/how-to-use-sie-audit-files-export)|You can import and export general ledger data according to the standard import export (SIE) format. By specifying SIE dimensions and file types, you can define the level of detail that's covered by import or export transactions.|

### Features generally available in 24

The following features are generally available. However, they aren't turned on by default, so to use them your administrator must manually enable them.

* [Feature: Enable legacy locking scheme in AL](https://go.microsoft.com/fwlink/?linkid=2244711). This key replaced the **Feature: Enable Tri-State locking in AL** key, which was enabled by default.

## 2023 release wave 2 (version 23)

### Features mandatory in version 23

These features are no longer controlled in **Feature management**, so they can't be disabled.

|Feature  |Description  |
|---------|---------|
|[Feature Preview: Analysis mode, quickly analyze data directly in Business Central](/dynamics365/release-plan/2023wave2/smb/dynamics365-business-central/analyze-group-pivot-data-list-pages-using-multiple-tabs)  |End users and data analysts can analyze data from list pages directly in the client without the need to open the page in Excel or run a report. The ability to analyze data directly in list pages raises the bar for what you can do without having to switch applications, while still allowing customers and partners to do more in report objects, Excel, Power BI, or other data analysis applications.  |
|[Feature: Enable using Form 1096 to transmit paper Tax Forms to the IRS in the United States](/dynamics365-release-plan/2022wave2/smb/dynamics365-business-central/irs-1096-form-united-states)  |Form 1096 is used to transmit paper forms 1097, 1098, 1099, 3921, 3922, 5498, and W-2G to the IRS. You can now run the Form 1096 report and send it to the IRS if it's required for them. Because [!INCLUDE [prod_short](../developer/includes/prod_short.md)] reports only Form 1099, the new Form 1096 is related only to any already transmitted 1099 paper forms.  |
|[Feature: Enable using of Service Declaration (Intrastat for Services)](/dynamics365/business-central/finance-how-setup-use-service-declaration)  | In some EU countries/regions, authorities require that businesses report the export of services to other EU countries/regions. The Service Declaration extension lets you collect information about service trade in the EU and report it to the authorities. Although it's named Service Declaration, you can also use it as Intrastat for Services. This extension is available for all EU countries/regions as a W1 version, and it can be used as-is in Belgium.  |
|[Feature Update: Standardized bank reconciliation and deposits.](/dynamics365-release-plan/2022wave1/smb/dynamics365-business-central/standardizing-bank-reconciliation-process-north-american-versions?branch=main&branchFallbackFrom=pr-en-us-2746)|Bank reconciliation in the North American (NA) versions for the United States, Canada, and Mexico can be done either through the standard **Bank Reconciliation** page or with the **Bank Rec. Worksheet** page, which was missing some of the newer features that the **Bank Reconciliation** page offers. To standardize the bank reconciliation process, we have modified the **Bank Reconciliation** page, added a feature for deposits that is the same as we provide for the NA version today, and added capabilities to allow users to reconcile deposits.|

### Features generally available in version 23

The following features are generally available. However, they aren't turned on by default, so to use them your administrator must manually enable them.

|Feature  |Description  |
|---------|---------|
|[Feature Update: Enable use of new extensible invoice posting engine](/dynamics365/release-plan/2023wave1/smb/dynamics365-business-central/extend-general-ledger-posting-aggregations)  |Regulations in different countries/regions and industries, and customer business practices, might require a change to how general ledger entries are aggregated during posting. We remove the dependencies from the Invoice Posting Buffer table in the base application and build an invoice posting component with an interface and an extensible enum for the implementation setup. This refactoring makes the posting process for sales, purchase, and service transactions extensible.  |
|[Feature Update: Enable use of new extensible exchange rate adjustment, including posting review](/dynamics365/release-plan/2023wave2/smb/dynamics365-business-central/adjust-exchange-rates-easily-replace-built-in-batch-job)  |When companies operate in multiple countries or regions, it's important that they can do business and run financial reports in more than one currency. Because exchange rates often change, businesses must periodically update the rates in [!INCLUDE [prod_short](../developer/includes/prod_short.md)]. This feature update gives accountants more control over how they adjust exchange rates. At the same time, it allows partners to extend and customize an exchange rate adjustment to meet the needs of specific industries or markets.  |
|[Feature Update: Enable Tri-State locking in AL](/dynamics365/release-plan/2023wave2/smb/dynamics365-business-central/performance-gain-reducing-locks-database)  |The tri-state locking feature is aimed at enhancing the performance and concurrency of database transactions. By enabling this feature, AL-based read operations that follow write operations are performed optimistically, rather than with strict consistency and low concurrency. Consequently, users can expect higher levels of concurrency and fewer blocked or failed operations while accessing data. [Learn more about tri-state locking](../developer/devenv-tri-state-locking.md).  |

<!--

Coming soon...

|Feature  |Description  |
|---------|---------|
|**Feature Update: Use the platform table 'Report Layout List' for adding and selecting layouts in the 'Report Selection' pages**  | Users can choose which report layout to use on the request page. This will make it easier to use different report layouts for different purposes, especially for Excel layouts. |

-->

<!-- v24
### Features postponed from becoming mandatory in 2023 Release Wave 2

The change to making these features mandatory is postponed. They aren't turned on by default and must be enabled manually. Use the links to learn more about them in the [!INCLUDE [prod_short](../developer/includes/prod_short.md)] release plans.

|Feature  |Description  |Expected to be mandatory release wave |
|---------|---------|-|
|[Feature: Create AI-powered product descriptions with Copilot](/dynamics365/release-plan/2023wave1/smb/dynamics365-business-central/drive-sales-ai-generated-product-descriptions) | Great products deserve great marketing, but authoring compelling product descriptions for dozens or even hundreds of similar products for your online store requires time, skill, and creativity. [!INCLUDE [prod_short](../developer/includes/prod_short.md)] accelerates time to market with AI-generated product descriptions, right from where you manage your inventory. We've streamlined the end-to-end process, starting from uploading a picture to [!INCLUDE [prod_short](../developer/includes/prod_short.md)], to AI-powered suggestions for marketing copy based on your product attributes such as color and material, to publishing that to your online store with just a few clicks. |2024 release wave 1 |-->

<!--v24
|Feature  |Description  |Expected to be mandatory release wave |
|---------|---------|-|
|[Feature Update: Legacy list views are hidden](/dynamics365-release-plan/2022wave2/smb/dynamics365-business-central/legacy-list-views-are-hidden)  | Legacy views are list views that were created by developers in previous versions of [!INCLUDE [prod_short](../developer/includes/prod_short.md)] by placing them on the role center page. [!INCLUDE [prod_short](../developer/includes/prod_short.md)] displays legacy views side by side with modern views directly on the list page, but legacy views offer a degraded experience and fewer options compared to modern views.|2024 release wave 1 |-->

<!-- now 28
|Feature  |Description  |Expected to be mandatory release wave |
|---------|---------|-|
|[Feature Update: Auto-save with every field change](/dynamics365-release-plan/2022wave2/smb/dynamics365-business-central/auto-save-as-work)  | [!INCLUDE [prod_short](../developer/includes/prod_short.md)] immediately saves changes to individual fields as soon as you tab away from the field or set focus to another element on the page, instead of only saving when the page is closed. Changes are saved to the database without any noticeable impact to performance. |2024 release wave 2 |

<!-- now 28
|Feature  |Expected to be mandatory release wave |
|---------|---------|
|[Use new sales pricing experience](/dynamics365-release-plan/2020wave2/smb/dynamics365-business-central/use-new-sales-pricing-experience-)     | 2025 release wave 1        | -->

## 2023 release wave 1 (version 22)

### Features mandatory in version 22

These features are no longer controlled in **Feature management**, so they can't be disabled.

|Feature  |Description  |
|---------|---------|
|[Check Documents and Journals while you work](/dynamics365-release-plan/2022wave1/smb/dynamics365-business-central/check-documents-journals-background)     | To alert you about issues with data in documents and journals that can prevent you from posting, we've introduced validations that identify issues right away. Early, unobtrusive visual indications of a problem can help improve productivity and save time. You can still control documents and check journal data for all users by turning on the **Enable Data Check** toggle on the **General Ledger Setup** page or, for individual users, by choosing **Enable Data Check** on the **My Notifications** page.        |
|[Auto-accept transactions for intercompany journals](/dynamics365-release-plan/2022wave1/smb/dynamics365-business-central/intercompany-postings-have-auto-accept-transaction-enabled-intercompany-general-journals)     | Intercompany postings make accounting for two or more companies easier for a centralized finance department or bookkeepers in intercompany partner companies. We've automated the task of accepting general journals, which removes several manual steps in the intercompany accounting process.        |
|[Use currency symbol in data synchronization with Dataverse](/dynamics365-release-plan/2021wave2/smb/dynamics365-business-central/use-currency-symbol-data-synchronization-dataverse)     | Including currency symbols with amounts makes it easier to visually scan and understand financial figures. If your [!INCLUDE [prod_short](../developer/includes/prod_short.md)] is integrated with Microsoft Dataverse, you can now synchronize currency symbols between the two apps.        |
|[Map to Dataverse option sets such as payment terms, freight terms, and shipping agents without code](/dynamics365-release-plan/2022wave1/smb/dynamics365-business-central/map-dataverse-option-sets-such-as-payment-terms-freight-terms-shipping-agents-without-code)    | Payment terms, shipment methods, and shipping agents can change along with the environments in which businesses operate. To react quickly to changing business conditions, businesses must be able to quickly and cost effectively change their payment, shipping, or freight policies across their business systems.        |
|[Log emails using a shared mailbox and Graph API](/dynamics365-release-plan/2022wave1/smb/dynamics365-business-central/log-emails-using-shared-mailbox-graph-api)     | Get more out of the communications between salespeople and your existing or potential customers by tracking email exchanges and turning them into actionable opportunities. [!INCLUDE [prod_short](../developer/includes/prod_short.md)] can work with Microsoft Exchange Online to keep a log of the inbound and outbound messages.        |
|[Item variant code on demand forecasts](/dynamics365-release-plan/2021wave2/smb/dynamics365-business-central/item-variant-code-demand-forecasts)     | Accurate demand forecasting gives businesses valuable insight into their position in the market, which helps decision makers shape their strategies for pricing, business growth, and market potential. The ability to include the right level of detail on item variants in demand forecasts unlocks planning capabilities and reduces lead times for companies that don't have an inflow of sales orders and manage many nearly identical items.        |
|[Support inventory pick and warehouse pick operations for jobs](/dynamics365-release-plan/2022wave1/smb/dynamics365-business-central/support-inventory-pick-warehouse-pick-operations-jobs)     | Businesses can switch on warehouse activities for jobs to help drive an effective flow through the warehouse and to organize and maintain inventory.        |
|[Report read-only data access](/dynamics365/business-central/admin-data-access-intent)     | You can set up [!INCLUDE [prod_short](../developer/includes/prod_short.md)] to use read-only replicas of the primary (read-write) database. Using the database replica reduces the load on the primary database. In some cases, it will also improve the performance when viewing data in the client. Replicas benefit objects, like reports, queries, and API pages, that are used for viewing data only, not modifying data.        |
|[Unlock time sheets in Business Central using assisted setup and data entry on mobile devices](/dynamics365-release-plan/2021wave2/smb/dynamics365-business-central/unlock-time-sheets-business-central-using-assisted-setup-data-entry-mobile-devices)     | Getting to that first time sheet entry should be as painless as possible. Many employees use time sheets. As the time sheet administrator or manager, you want to make sure that [!INCLUDE [prod_short](../developer/includes/prod_short.md)] has you covered when you create time sheets for the first time, or you add an employee or resource to record the time spent on tasks.A busy professional on the road using mobile devices (Android or iOS) needs to be able to provide time sheet entries in an easy and productive way while on the go.        |

### Features enabled by default in version 22

These features are turned on by default for new customers, but you can still manually disable them. Use the links to learn more about them in the [!INCLUDE [prod_short](../developer/includes/prod_short.md)] release plans.

|Feature  |Description  |
|---------|---------|
|[Convert user group permissions](/dynamics365/release-plan/2023wave1/smb/dynamics365-business-central/manage-user-permissions-using-security-groups)     | As businesses grow and change, managing permissions can become increasingly complex. Security groups can simplify the process by allowing administrators to group users by department, job function, or other criteria, and assign permissions to the group as a whole. Using security groups to manage permissions can save time and reduce the risk of human error. Security groups allow for easier management of access control, ensuring that users only have access to the resources they need. This feature can also streamline the process of onboarding new employees or contractors, as they can be quickly added to the appropriate security groups.        |
|[New approval workflow experience with Power Automate templates](/dynamics365/release-plan/2023wave1/smb/dynamics365-business-central/new-approval-workflow-experience-templates-power-automate)     | Advanced and flexible approval workflows don't need to be complex. Business owners or decision makers can choose from multiple templates when they set up approval workflows in [!INCLUDE [prod_short](../developer/includes/prod_short.md)].        |

### Features generally available in version 22

These features are now generally available. They aren't turned on by default and must be enabled manually.

* [Replace the existing Automatic Account Codes functionality with the new Automatic Account Codes extension](/dynamics-nav-app/localfunctionality/sweden/automatic-account-codes)
* [Feature Update: Use new customer and item templates in Shopify instead of the generic templates](https://go.microsoft.com/fwlink/?linkid=2224515)
* [Enable using SIE Audit Files Exports](/dynamics365/business-central/localfunctionality/sweden/how-to-import-and-export-data-in-standard-import-export-format)

<!--
### Features postponed from becoming mandatory in 2023 Release Wave 1

The change to making these features mandatory is postponed. They aren't turned on by default and must be enabled manually. Use the links to learn more about them in the [!INCLUDE [prod_short](../developer/includes/prod_short.md)] release plans.

|Feature  |Expected to be mandatory release wave |
|---------|---------|
|[Use tracking by package number in reservation and tracking system](/dynamics365/business-central/inventory-how-setup-item-tracking)     |  2024 release wave 1       |
|[New Microsoft Word report rendering platform](/dynamics365/business-central/dev-itpro/developer/devenv-howto-report-layout)     | 2024 release wave 1        |
|[Replace Multiple Interest Rate CZ with Finance Charge Interest Rate](/dynamics365/business-central/receivables-collect-outstanding-balances)| 2025 release wave 2 |
| [Use new sales pricing experience](/dynamics365-release-plan/2020wave2/smb/dynamics365-business-central/use-new-sales-pricing-experience-)||-->

## Related information

[Enabling Upcoming Features Ahead of Time](feature-management.md)  
[Deprecated Features in the Base App](../upgrade/deprecated-features-w1.md)
