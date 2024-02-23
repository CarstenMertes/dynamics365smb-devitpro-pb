---
title: Integrating with Microsoft Dataverse
description: Learn how to integrate Business Central with Microsoft Dataverse
author: kennienp
ms.reviewer: solsen
ms.topic: overview
ms.author: kepontop
ms.date: 02/02/2024
---

# Integrating Business Central with Microsoft Dataverse

Business apps often use data from more than one source. Microsoft Dataverse combines data into a platform that makes it easier to connect [!INCLUDE[prod_short](../includes/prod_short.md)] to other Dynamics 365 applications. For example, Dynamics 365 Sales or your own application built on [!INCLUDE[dataverse_short](../includes/dataverse_short.md)].

There are four types of complementary app/system interactions between [!INCLUDE[prod_short](../includes/prod_short.md)] and [!INCLUDE[dataverse_short](../includes/dataverse_short.md)]: 

- Data synchronization that replicates data between [!INCLUDE[prod_short](../includes/prod_short.md)] and [!INCLUDE[dataverse_short](../includes/dataverse_short.md)].
- Data virtualization with virtual tables in [!INCLUDE[dataverse_short](../includes/dataverse_short.md)] via [!INCLUDE[prod_short](../includes/prod_short.md)] API for (**C**reate/**R**ead/**U**pdate/**D**elete) operations.
- Data change ((**C**reate/**U**pdate/**D**elete)) events using webhooks.
- Business events.

:::image type="content" source="media/connect-to-dataverse.svg" alt-text="Shows the four interactions of DataVerse with Business Central" lightbox="media/connect-to-dataverse.svg":::


## Data synchronization

You can synchronize data either to or from one Dynamics 365 business app to another, or in both directions in near-real time, through [!INCLUDE[dataverse_short](../includes/dataverse_short.md)]. This persists the synchronized data on the destination end of the setup.

[![Shows how data synchronization works between Business Central and Dataverse](media/data-synchronization-between-Business-Central-and-Dataverse.svg)](media/data-synchronization-between-Business-Central-and-Dataverse.svg#lightbox)

For more information, see [Integrate with Dataverse via data sync](/dynamics365/business-central/admin-common-data-service).

## Data virtualization

Virtual tables in [!INCLUDE[dataverse_short](../includes/dataverse_short.md)] can use [!INCLUDE[prod_short](../includes/prod_short.md)] APIs exposed through API Pages. As seen from [!INCLUDE[dataverse_short](../includes/dataverse_short.md)], these virtual tables act as regular tables. 

[![Shows how data virtualization works between Business Central and Dataverse](media/dataverse-virtual-tables.svg)](media/dataverse-virtual-tables.svg#lightbox)

Makers can now build experiences in apps built on [!INCLUDE[dataverse_short](../includes/dataverse_short.md)] with live data shown from [!INCLUDE[prod_short](../includes/prod_short.md)] and with full CRUD capability. All data changes are only saved in [!INCLUDE[prod_short](../includes/prod_short.md)], so no data is copied to Microsoft Dataverse. 

For more information, see [Integrate with Microsoft Dataverse via virtual tables](../powerplatform/powerplat-overview.md).   


## Data change events

Webhooks is a way to get notified if an entity exposed to an API changes in [!INCLUDE[prod_short](../includes/prod_short.md)]. For example, you can use webhook notifications to trigger Power Automate flows from events in [!INCLUDE[prod_short](../includes/prod_short.md)]. 

For more information, see [Data change (CUD) events](../api-reference/v2.0/dynamics-subscriptions.md).

## Business events (preview)

Business events provide a mechanism for notifying [!INCLUDE[dataverse_short](../includes/dataverse_short.md)] when actions are done on [!INCLUDE[prod_short](../includes/prod_short.md)]. As an example, you can use Power Automate to subscribe to [!INCLUDE[prod_short](../includes/prod_short.md)] for its business events and interact with other apps in the Dynamics ecosystem, such as Dynamics 365 Sales or Customer Service, and others built using Power Apps. 

For more information, see [Business events](../developer/business-events-overview.md).


## See also

[Integrate with Dataverse via data sync](/dynamics365/business-central/admin-common-data-service)  
[Integrate with Microsoft Dataverse via virtual tables](../powerplatform/powerplat-overview.md)   
[Data change (CUD) events](../api-reference/v2.0/dynamics-subscriptions.md)  
[Business events (preview)](../developer/business-events-overview.md)  
