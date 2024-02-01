---
title: Migrate Dynamics GP data to the cloud
description: Learn how to migrate to the cloud from Dynamics GP using an assisted setup guide in Business Central online. Move historical data to Azure Data Lake.
author: jenolson

ms.topic: conceptual
ms.devlang: al
ms.reviewer: jswymer
ms. search.keywords: cloud, edge, gp, migration
ms.search.form: 4003
ms.date: 08/23/2022
ms.author: jswymer
---

# Migrate Dynamics GP Data to the Cloud

An assisted setup guide in [!INCLUDE [prod_short](../developer/includes/prod_short.md)] can help you migrate data from Dynamics GP. You can migrate data from Dynamics GP 2015 and later versions of Dynamics GP. For more information, see [System requirements](faq-migrate-data.md#system-requirements).  

> [!IMPORTANT]
> Migrating from Dynamics GP using the **Cloud Migration Setup** assisted setup guide is currently only supported for the following markets: United States, Canada, United Kingdom, Australia.

The end-to-end process is described [here](migrate-data.md). In this article, we talk about background information and things to take into consideration.  

As part of the Business Central 21.1 release, company settings for data migration have been moved from the Cloud Migration Setup Wizard and placed in a new GP Company Migration Configuration page.  This page allows for improved ease of use by allowing you to make global settings for all companies selected to migrate with the ability to update at a company level if necessary.  You can access the GP Company Migration Configuration page from Migration Management.

In addition to the GP Company Migration Configuration page you can select which modules you would like migrated from GP to Business Central. You will be able to select from the following modules to migrate: Accounts Payable, Accounts Receivable, Bank, Open Purchase Orders and Inventory.

*Note: General Ledger information will always be migrated.*  


## Dynamics GP data

Business Central update 21.1  adds a new page, **GP Company Migration Configuration**. Use this new page to select the data you want migrated from Dynamics GP to Business Central. The page will automatically open after you complete the **Cloud Migration Setup** wizard, but you can also open it from the **Cloud Migration Management** page.  

New options such as selecting what modules you want to migrate as well as if you only want to migrate master data for specific modules are available.  You can select the options at a global level, applying the options to all companies selected to migrate or you can tweak options at a company level in the Per Company fast tab.  
 
If you select to only migrate master data, records such as Accounts, Customer, Vendors and Items will migrate, however no transactional information from GP will be migrated for the selected module.    

When you migrate from Dynamics GP, the following information is migrated from Dynamics GP to Business Central online:

1. Fiscal periods

    The *fiscal periods setup* in Dynamics GP will be migrated to Business Central as *accounting periods*. Any years marked as *historical* in Dynamics GP will come over to Business Central as *open* and will must be closed in Business Central. If any adjustments need to be made to historical years after migrating, those adjustments can be done before closing the year.  

2. Chart of Accounts master records

    The account number in Business Central will be mapped from the main account segment from Dynamics GP. Remaining account segments are then defined as [dimensions](/dynamics365/business-central/finance-dimensions/) in [!INCLUDE [prod_short](../developer/includes/prod_short.md)]. The GP Company Migration Configuration asks the user to enter a segment for *Global Dimension 1* and *Global Dimension 2*. If your chart of accounts in Dynamics GP has more than 2 segments outside of the main segment, the other segments are automatically set up as shortcut dimensions (3-8). You can verify the setup in the **General Ledger Setup** page in Business Central.

    Let us look at an example of an account from Dynamics GP, using the year 2022 as an example:

    |Account in Dynamics GP |Year|Name  |Amount  |
    |-----------------------|----|------|--------|
    |000-1100-00  Cash |Yes 2022 |  |  |
    |     |  |Period 1| 250.00 |
    |     |  |Period 2 | 117.00 |
    |     |  |Period 3 |340.00 |
    |000-1100-01  Cash |Yes 2022 |  |  |
    |     |  |Period 1| 240.00 |
    |     |  |Period 2 | 102.00 |
    |     |  |Period 3 |501.00 |
    |000-4000-00 Sales |Yes 2022 |  |  |
    |     |  |Period 1| 490.00 |
    |     |  |Period 2 | 219.00 |
    |     |  |Period 3 |841.00 |

    The migration creates two accounts in [!INCLUDE [prod_short](../developer/includes/prod_short.md)], number 1100 and number 4000. New dimensions are also added with the names 000, 00, and 01. General journal transactions are created as follows:

    |Transaction date |Account No.|Amount  |Dimensions|
    |-----------------|-----------|--------|----------|
    |1/31/2022        |1100   |250.00 |Dimension 000, 00|
    |1/31/2022        |1100   |240.00 |Dimension 000, 01|
    |1/31/2022        |4000   |490.00 |Dimension 000, 00|
    |2/28/2022        |1100   |117.00 |Dimension 000, 00|
    |2/28/2022        |1100   |102.00 |Dimension 000, 01|
    |2/28/2022        |4000   |219.00 |Dimension 000, 00|
    |3/31/2022        |1100   |340.00 |Dimension 000, 00|
    |3/31/2022        |1100   |501.00 |Dimension 000, 01|
    |3/31/2022        |4000   |841.00 |Dimension 000, 00|

    The data migration generates dimensions on that account based on the different segments. User will see a *Department* dimension with the values *000*, *100*, and *200*, respectively. A second dimension, *Division*, will show the values *00*, *01*, and *02*, respectively.

      Account summary transactions are generated and posted for open and history years that were set up in Dynamics GP. The summary amounts are created based on the fiscal periods set up in Dynamics GP. In the GP Company Migration Configuration page, you can select the oldest historical year you want migrated to Business Central. For example, if 2019, 2020, and 2021 are historical years in Dynamics GP, you could select that the oldest historical year you want migrated is 2020. Summary transactions for 2019 would not be migrated to Business Central.

3. Customer master records and outstanding transactions from the Receivables module

    In the GP Company Migration Configuration page, you can choose to migrate all customers from Dynamics GP or only active customers. This allows you to not migrate over customers that have been marked as inactive. We also have added bringing all addresses from the customer over into Business Central. All of the addresses on the customer will be setup as shipping addresses in Business Central. That will allow the end user to choose the address needed when entering transactions after the migration.  

    In the GP Company Migration Configuration page, you can also choose to migration posting accounts on customer classes. If you choose this option, posting accounts defined on *customer classes* in Dynamics GP will be migrated to Business Central as *customer posting groups*. If a customer is assigned to a customer class in Dynamics GP, the customer will be assigned to the corresponding customer posting group after migrating.

    We also bring over outstanding receivables transactions. These transactions will be brought in with the amount remaining in Dynamics GP. For example, if an invoice for $1000 was entered into Dynamics GP, and it has been partially paid and has a remaining balance of $400, the new invoice created in Business Central will be for $600 as that is the amount remaining to be paid. We bring over all transaction types from Receivables Management.

4. Vendor master records and outstanding transactions from the Payables module

    In the GP Company Migration Configuration page, you can choose to migrate all vendors from Dynamics GP or only active vendors. This allows you to not migrate over vendors that have been marked as inactive. We also have added bringing all addresses from the vendor over into Business Central. All vendor addresses from the vendor are migrated to Business Central. The vendor's Remit To Address will be the main address for the vendor. All other vendor addresses will be setup as Order addresses in Business Central. That will allow the end user to choose the address needed when entering transactions after the migration.  

    In the GP Company Migration Configuration page, you can also choose to migrate posting accounts on vendor classes. If you choose this option, posting accounts defined on *vendor classes* in Dynamics GP will be migrated to Business Central as *vendor posting groups*. If a vendor is assigned to a vendor class in Dynamics GP, the vendor will be assigned to the corresponding vendor posting group after migrating.

    Vendor EFT Bank information will be migrated to Business Central as Vendor Bank Accounts.  If a Vendor's Remit to address contains EFT Bank information in Dynamics GP, it will be migrated over as the Preferred Bank Account Code on a vendor in Business Central.

    We also bring over outstanding Payables transactions. These transactions will be brought in with the amount remaining in Dynamics GP. For example, if an invoice for $1000 was entered into Dynamics GP, and it has been partially paid and has a remaining balance of $400, the new invoice created in Business Central will be for $600 as that is the amount remaining to be paid. We bring over all transaction types from Payables Management.

   1099 vendor information and amounts can be migrated to Business Central.   An option has been added to the GP Company Migration Configuration page where you can select if you want to migrate 1099 information.    The tax type, Federal ID number and 1099 box number from the vendor record will be migrated.  In addition, the 1099 box amounts will be migrated for each 1099 vendor.   If you select to migration 1099 information, you will also indicate the calendar year for which you want to migrate 1099 amounts.  Note that the first supported year for migrating 1099 information is 2022.    

    You can also bring over Open Purchase Orders. When we migrate purchase orders, we are looking at the items and the quantities remaining on those items to determine what we will bring over as an open purchase order. If an item is fully received and invoiced that item will not migrate. By bringing over open purchase orders, you do not have to enter outstanding transactions from the purchase order aspect.

5. Inventory items

    Inventory is imported with the cost valuation method that is set in GP at the time the migration is run. Location information as well as the quantity on hand for each time is migrated. If serial or lot information is tracked on an item, that information is also migrated.  

    In the GP Company Migration Configuration page, you can choose to migrate posting accounts on item classes. If you choose this option, posting accounts that are defined on *item classes* in Dynamics GP will be migrated to Business Central as *inventory posting groups*. If an item is assigned to an item class in Dynamics GP, the item will be assigned to the corresponding inventory posting group after migrating. If you only want to migrate active items you can choose to exclude inactive items in the GP Company Migration Configuration page.  Additional, you can choose if you do not want to migrate discontinued items.  
 
6. Checkbook transaction and master data 

    You can choose to migrate all checkbooks from Dynamics GP or only active checkbooks. Unreconciled bank transactions will be migrated to Business Central so that you can reconcile your checkbooks after migrating.  Any cash receipt that has been posted should also be deposited in GP before migrating, as undeposited receipts will not migrate. 

7. GP Historical Snapshot 

    In the GP Company Migration Configuration page you can select if you want to migrate historical information from GP into Business Central. This data will be visible in listpages found under the corresponding entities and navigating to GP Detail Snapshot. You can indicate if you want to migrate GL detail, Receivables, Payables, Sales Order Processing, Purchase Order Receipts and Inventory transactions.  The data is stored in extension tables in Business Central.  Data stored in those tables can be used in Power BI reports, Power Apps or other 3rd party reporting tools.   The tables containing the GP Historical Snapshot data are as follows:

    - Hist. G/L Account
    - Hist. Gen. Journal Line
    - Hist. Payables Document
    - Hist. Receivables Document
    - Hist. Sales Trx. Header
    - Hist. Sales Trx. Line
    - Hist. Purchase Recv. Header
    - Hist. Purchase Recv. Line
    - Hist. Inventory Trx. Header
    - Hist. Inventory Trx. Line

    You can limit the about of data migrated in the snapshot by entering the latest year in GP that you want brought over.  Enter this year in the Oldest GP Year field in the GP Company Migration Configuration page.  

    The GP Historical Snapshot will run as a background process after the migration is complete.  The status of the GP Historical Snapshot data can be viewed in Fact boxes in the Cloud Migration Management page.
   
    
## Diagnostics run

In the **Cloud Migration Management** page, you can create a diagnostics run to do more data validation/verification before the migration is run so that you can decrease the risk of a failed migration.

The maximum field length is different in Dynamics GP (30) and [!INCLUDE [prod_short](../includes/prod_short.md)] (20), and the diagnostics run checks for issues and shows warnings. The tool also checks item numbers to look for duplicates based on the character limit, and it checks to make sure there are no blank posting accounts that are needed for posting of transactions with the migration.

Here is an example of what you might see when you run a diagnostic run:

:::image type="content" source="../media/gp-migration-diagnostics.png" alt-text="Status of migration run inside Business Central]":::

## Migration tool support for Australia

Starting with 2020 release wave 2, organizations in Australia can migrate from Dynamics GP to an Australian version of [!INCLUDE [prod_short](../includes/prod_short.md)] online.

The process to run the migration in an Australian [!INCLUDE [prod_short](../includes/prod_short.md)] online is the same as running a migration in the other supported countries/regions. However, there is some setup that needs to be done before the migration can be run. To make the changes to the setup, you must run through the cloud migration wizard. When the wizard setup is complete, and companies are fully set up, you must log into the companies that you are planning to migrate and make the following changes

* Transactions

  With transactions that are being migrated, we bring over totals on the invoices for the customers so GST information is already included in the transactions. You must turn off the GST and Adjustment Mandatory features in the **General Ledger Setup** page to allow the transactions to post during the migration. After the migration is complete, you can turn both GSP and Adjustment Mandatory back on so that new transactions that are entered in [!INCLUDE [prod_short](../includes/prod_short.md)] online will use this functionality.

* Posting groups

  Within the posting process there is validation to look for a blank VAT business posting group and VAT product posting group. This combination isn't setup by default and is needed for the migration. So add a VAT posting configuration in the **VAT Posting Setup** page with blank values for the **VAT Bus Posting Group** and **VAT Prod. Posting Group** fields.  

## <a name="lake"></a>Move your Dynamics GP database to Azure Data Lake

Starting with 2020 release wave 2, you can create a copy of the Dynamics GP database in Azure Data Lake so that you have it for future reference after the migration to [!INCLUDE [prod_short](../developer/includes/prod_short.md)] online. To take advantage of this functionality, there are some pieces that must be set up before the migration process. A customer is not required to copy their database to Azure Data Lake, but there are several benefits to being able to do so, including having access to the historical data that is not migrated by the migration tool. For an introduction to Azure Data Lake, see [azure.microsoft.com](https://go.microsoft.com/fwlink/?linkid=2135056).  

To create an Azure Data Lake storage account, you log in to your Azure subscription (or sign up for an Azure subscription). Once logged into the Azure portal, you can create a storage account. Under the **Access Keys** section of the information about your storage account in the Azure portal, you can see the keys that you must provide in the cloud migration wizard in [!INCLUDE [prod_short](../developer/includes/prod_short.md)]. For more information about Azure Data Lake and setting up a storage account, see [Azure documentation](/azure/storage/blobs/data-lake-storage-introduction).  

## To move to Azure Data Lake

1. In your [!INCLUDE [prod_short](../developer/includes/prod_short.md)] online tenant, choose the :::image type="icon" source="../media/search_small.png" border="false"::: icon, enter **Cloud Migration Management**, and then choose the related link.
2. Choose the **Azure Data Lake** action.

    The **Azure Data Lake Migration Setup** guide takes you through the steps to connect your on-premises Dynamics GP database and your storage in Azure Data Lake. You must have created an Azure Data Lake storage account (v2) before launching the assisted setup, and you must have access to the storage account name and storage account key.
3. When the setup completes, you can monitor the progress of moving your data from on-premises to Azure Data Lake in the **Cloud Migration Management** page in [!INCLUDE [prod_short](../developer/includes/prod_short.md)].

If you go back to the Azure portal, you can see the data that was moved from your Dynamics GP database to Azure Data Lake. Under the containers section of the Data Lake storage, a new *gp-database* folder contains the company/system databases, and sub-folders contain the series folder and data files.  

The database folder in Azure Data Lake will always be set as *gp-database*. If you want to rename it, you can do so after the migration has competed. The same applies to the various sub-folders. The folders created follow the standard naming convention of the *series* folders in Dynamics GP. An additional folder, *3rd Party*, will be created, and any files that haven't be mapped to a folder will reside in there. You can modify the content in the folders after the migration has completed.

If an Azure Data Lake migration has already been run in the [!INCLUDE [prod_short](../developer/includes/prod_short.md)] company and you launch a second run, the migration tool will check to see if a *gp-database* folder exists. If you still want to run the migration again, you must delete the *gp-database* folder and its contents before you can run the wizard again.  

At the end of the migration, you have a completely copy of your Dynamics GP database in the cloud with all the advantages of having access to historical data without having to maintain a server on-premises.  

## See also

[Run the assisted setup guide](migrate-gp-overview.md#run-the-assisted-setup-guide)  
[Compare Work in Dynamics GP to Business Central](migrate-dynamics-gp-videos.md)  
[Migrating On-Premises Data to Business Central Online](migrate-data.md)  
[Troubleshooting Cloud Migration](migration-troubleshooting.md)  
[FAQ about Migrating to Business Central Online from On-Premises Solutions](faq-migrate-data.md)  
