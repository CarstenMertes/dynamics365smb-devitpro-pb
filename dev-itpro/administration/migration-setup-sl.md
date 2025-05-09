---
title: Run cloud migration setup for Dynamics SL migration
description: Learn how to run Cloud Migration Setup to configure the components and connection to migrate from a Dynamics SL on-premises to Business Central online.
author: lcontreras
ms.author: jswymer
ms.reviewer: jswymer
ms.topic: how-to 
ms.date: 12/13/2024
ms.custom: bap-template
---
# Run cloud migration setup for Dynamics SL migration

This article explains how to run the **Cloud Migration Setup** guide to configure the components and connection for migrating data from a Business Central on-premises database to a Business Central online environment. Learn more in [Cloud migration setup overview](migration-setup-overview.md).

This article explains how to run the **Cloud Migration Setup** guide to configure the components and connection for migrating data from a Business Central on-premises database to a Business Central online environment. For more information about the setup, go to [Cloud migration setup overview](migration-setup-overview.md).

[!INCLUDE [migrate-e2e-process](../developer/includes/migrate-e2e-process-SL.md)]

## About delegated administrators

Any user running the cloud migration setup flow as a delegated administrator must get approval from a licensed user to run the cloud migration. The licensed user must have an *Essentials* or the *Premium* license and SUPER permissions. In this case, the **Cloud Migration Setup** assisted setup guide displays an extra step, where the delegated administrator can copy the autogenerated approval link and send it to the licensed user for approval. Once the licensed user approves the request, the delegated administrator can continue with the setup of the cloud migration and perform all other steps required to complete that process. The licensed user can always revoke the permission to run the migration by choosing the same approval link that was shared by the delegated administrator, or from the **Cloud Migration Approval** page.  

## Prepare

- Review [Check prerequisites](cloud-migration-prerequisites-SL.md) and make sure the environments meet the requirements.

   > [!IMPORTANT]
   > [!INCLUDE [bc-cloud-migrate-prod](../includes/bc-cloud-migrate-prod.md)]

- Review [Retain permissions](migration-retain-permissions-SL.md) if you have users already in your Business Central online environment and want them to continue working as usual during cloud migration.

> [!TIP]
> We recommend that you start the migration by running the assisted setup from a company other than the company to which you're migrating data. For example, sign into the demonstration company, CRONUS, and start the process there. This way, you can make sure that all users are logged out of the original company and the target company.
>
> Be aware of the storage capacity of your online tenant. If you need more than the default 80 GB, you can buy additional environments or storage capacity. Storage capacity is determined as 80 GB + allowances per licensed Essential/Premium user + any storage capacity licenses. Learn more in [Managing Capacity](../administration/tenant-admin-center-capacity.md).

## Run the cloud migration setup

1. [Sign in to the Microsoft 365 tenant](https://admin.microsoft.com) used by [!INCLUDE [prod_short](../includes/prod_short.md)] online.

   The person who sets up and runs the cloud migration must be signed in as an administrator of the Microsoft Entra (Microsoft 365) tenant and [!INCLUDE [prod_short](../includes/prod_short.md)] online.
1. [Sign in to Business Central online](https://businesscentral.dynamics.com) and open the environment to which you're migrating the data.
1. From the **Settings** page, select the **Assisted Setup** option.
1. From the **Assisted Setup** page, select **Set up Cloud Migration**.
1. Read the information on the page and provided links. If you consent, switch on **I accept warning & privacy notice**, then select **Next**.
1. Set **Product** option to the version that matches the on-premises product that you're migrating, then select **Next**.
1. On the **Define your SQL database connection** page, fill in the information about the SQL database connection and integration runtime.

   For more information about this step, go to [Define your SQL database connection](#define-sql-database-connection-and-integration-runtime).

   Select **Next** when done. Once you choose **Next**, a new pipeline is created in the Azure service.

1. After the pipeline is created, the **Select companies to migrate** page appears. Select one or more companies from the list or switch on **All Companies**, then select **Next**.

1. When completed successfully, the **SL Company Migration Configuration** page appears. This page allows you to make global settings for the companies selected for migration in the previous step.

   Select the companies that you want to migrate and then select **Next**.

   If you want to add or remove companies later, you can return to this page. For more information about using this page, go to [Configure Dynamics SL company data migration](migrate-SL-configure-companies.md).

1. Select **Finish** to complete the cloud migration setup.

  To open **Cloud Migration Management** and run the migration, select **Yes**.

<a name="sql"></a>

[!INCLUDE[cloud-migration-sql-connection-ir](../developer/includes/cloud-migration-sql-connection-ir-SL.md)]

## Rerunning cloud migration setup guide

There are some scenarios where it might be necessary for you to run the cloud migration setup guide more than once.  

> [!TIP]
> We recommend that you take a backup of the target environment so that you can easily restore the environment to a specific state and time, should you want to do so.

A common scenario is when you want to add tenants to an existing runtime service. If you're a hosting partner, you might have multiple tenants running on the same integration runtime service. Each tenant is isolated in their own data pipeline. To add tenants to an existing integration runtime service, enter the name of the existing integration runtime service into this field. The integration runtime name can be found in the **Microsoft Integration Runtime Manager**. Learn more in [Create and configure a self-hosted integration runtime](/azure/data-factory/create-self-hosted-integration-runtime) in the Azure docs.

In this scenario, you're making updates to an existing runtime service. When you get to the point of the assisted setup guide where you can specify an existing runtime service name, open the Microsoft Integration Runtime Service Manager. Then enter the runtime name in the field; you aren't allowed to copy and paste. The runtime service identifies that you're making updates to an existing service and doesn't create a new one.  

Complete the steps in the wizard to update the runtime service. If the change is related to adding tenants to an existing service, a new data pipeline is created for that tenant. Regenerating an Azure Data Factory (ADF) key might be done using the **Cloud Migration Management** page in your [!INCLUDE[prod_short](../developer/includes/prod_short.md)] online. Learn more in [Run the assisted setup guide](migration-setup-SL.md#rerunning-cloud-migration-setup-guide).  

## Troubleshoot and fix problems

If you encounter problems with the setup, learn more in [Cloud migration troubleshooting for Business Central](/troubleshoot/dynamics-365/business-central/welcome-business-central).

## Next steps

[Run data replication](migration-data-replication.md)

## Related information

[Dynamics SL migration to Business Central online: End-to-end overview](migrate-SL-overview.md)  
[Compare work in Dynamics SL to Business Central](migrate-dynamics-SL-videos.md)  
[FAQ about migrating to Business Central Online from on-premises solutions](faq-migrate-data.md)
