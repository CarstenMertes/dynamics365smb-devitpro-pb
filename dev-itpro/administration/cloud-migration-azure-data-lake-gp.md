---
title: Move Dynamics GP database to Azure Data Lake
description: Learn how to create a copy of the Dynamics GP database in Azure Data Lake so that you have it for future reference after the migration.
author: jswymer
ms.author: jswymer
ms.reviewer: jswymer
ms.topic: how-to 
ms.collection: 
ms.date: 02/29/2024
ms.custom: bap-template
---
# Move Dynamics GP database to Azure Data Lake

You can create a copy of the Dynamics GP database in Azure Data Lake so that you have it for future reference after the migration to [!INCLUDE [prod_short](../developer/includes/prod_short.md)] online. To take advantage of this functionality, there are some pieces that must be set up before the migration process. A customer isn't required to copy their database to Azure Data Lake. But there are several benefits to being able to do so, including having access to the historical data that isn't migrated by the migration tool. For an introduction to Azure Data Lake, see [azure.microsoft.com](https://go.microsoft.com/fwlink/?linkid=2135056).  

To create an Azure Data Lake storage account, you sign in to your Azure subscription (or sign up for an Azure subscription). Once signed into the Azure portal, you can create a storage account. Under the **Access Keys** section of the information about your storage account in the Azure portal, you can see the keys that you must provide in the cloud migration management in [!INCLUDE [prod_short](../developer/includes/prod_short.md)]. For more information about Azure Data Lake and setting up a storage account, see [Azure documentation](/azure/storage/blobs/data-lake-storage-introduction).  

## Prerequisites

You have an Azure Data Lake Gen2 storage account with access to the storage account name and storage account key. <!--Learn more about creating an [Azure Data Lake storage account](/azure/storage/common/storage-account-create?toc=%2Fazure%2Fstorage%2Fblobs%2Ftoc.json&bc=%2Fazure%2Fstorage%2Fblobs%2Fbreadcrumb%2Ftoc.json&tabs=azure-portal).-->

## Move to Azure Data Lake

1. Sign in to your [Business Central online](https://businesscentral.dynamics.com) tenant.
1. In the upper-right corner, select the ![Shows the search magnifyting glass icon](../developer/media/search_small.png) icon, enter **Cloud Migration Management**, and then choose the related link to open the **Cloud Migration Management** page.
1. In the action bar along the top, select **...** (Show the rest) > **Actions** > **Azure Data Lake**.

    The **Azure Data Lake Migration Setup** guide takes you through the steps to connect your on-premises Dynamics GP database and your storage in Azure Data Lake. 
1. When the setup completes, you can monitor the progress of moving your data from on-premises to Azure Data Lake in the **Cloud Migration Management** page in [!INCLUDE [prod_short](../developer/includes/prod_short.md)].

If you go back to the Azure portal, you can see the data that was moved from your Dynamics GP database to Azure Data Lake. Under the containers section of the Data Lake storage, a new *gp-database* folder contains the company/system databases, and subfolders contain the series folder and data files.  

The database folder in Azure Data Lake is always set to *gp-database*. If you want to rename it, you can do so after the migration completes. The same applies to the various subfolders. The folders created follow the standard naming convention of the *series* folders in Dynamics GP. Another folder, *3rd Party*, is created, and any files that haven't been mapped to a folder reside in this folder. You can modify the content in the folders after the migration completes.

If an Azure Data Lake migration has already run in the [!INCLUDE [prod_short](../developer/includes/prod_short.md)] company, and you launch a second run, the migration tool checks to see if a *gp-database* folder exists. If you still want to run the migration again, you must delete the *gp-database* folder and its contents before you can run the wizard again.  

At the end of the migration, you have a complete copy of your Dynamics GP database in the cloud with all the advantages of having access to historical data without having to maintain a server on-premises.  

## Next steps

- [Run cloud migration setup](migration-setup-gp.md)
- [Run data migration](migration-data-replication.md)
- [Run data upgrade](migration-data-upgrade-gp.md)
- [Complete cloud migration](migration-finish-gp.md)  

## Related information

[Dynamics GP migration to Business Central online: End-to-end overview](migrate-gp-overview.md)  
[FAQ about migrating to Business Central online from on-premises solutions](faq-migrate-data.md)  
