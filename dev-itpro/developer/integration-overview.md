---
title: Integration overview for Business Central online
description: Find links to information about the ways you can integrate Business Central to products and services.
author: kennienp
ms.reviewer: solsen
ms.topic: overview
ms.author: kepontop
ms.date: 02/05/2024
---

# Integration overview for Business Central online

This article is intended to help architects and developers make sound design decisions when they implement integration scenarios to and from [!INCLUDE[prod_short](../includes/prod_short.md)].

The article describes integration patterns, integration scenarios, and integration solutions. However, it doesn't include technical details about how to use or set up every integration pattern. It also doesn't include sample integration code.

## Integrations to/from Business Central are done with web services

All integrations to/from [!INCLUDE[prod_short](../includes/prod_short.md)] are done using web services. [!INCLUDE[prod_short](../includes/prod_short.md)] supports three types of web services: REST API, SOAP, and OData. 

[![Shows the three different types of web services in Business Central](media/webservice-stack.svg)](media/webservice-stack.svg#lightbox)


The recommended way to expose a web service for [!INCLUDE[prod_short](../includes/prod_short.md)] is using the REST API stack. 

For more information, see [Web services overview](../webservices/web-services.md).

## How to explore and develop against Business Central REST APIs

When you need to connect to [!INCLUDE[prod_short](../includes/prod_short.md)] from another application, you should use REST APIs, either the built-in APIs or custom APIs. 

[![Shows how the API stack in Business Central](media/api-stack.svg)](media/api-stack.svg#lightbox)

For more information on how to explore and develop against APIs, best practices, and which built-in APIs exist, see [REST API overview](../webservices/api-overview.md).


## Business Central connector for Power Platform

A *connector* is a proxy or a wrapper around an API that allows the user of the connector to talk to the underlying service. [!INCLUDE[prod_short](../includes/prod_short.md)] has its own connector that allows Power Platform products such as Power Automate, Power Apps, and Logic apps to communicate with 
[!INCLUDE[prod_short](../includes/prod_short.md)] through REST APIs (this is another reason for using REST APIs compared to OData/SOAP enabled pages/queries/codeunits).

[![Shows how the Power Platform connector integrates to Business Central](media/power-platform-connector-diagram.svg)](media/power-platform-connector-diagram.svg#lightbox)

For more information, see [Power Platform Connectors Overview](/connectors/connectors) and [Dynamics 365 Business Central Connector](/connectors/dynamicssmbsaas) in the Power Platform documentation.

## Connector: Integrating Business Central with Microsoft Power Apps

You can integrate [!INCLUDE[prod_short](../includes/prod_short.md)] with Microsoft Power Apps by using the [!INCLUDE[prod_short](../includes/prod_short.md)] connector for Power Platform. With Power Apps, you have the flexibility to build the perfect solution for your business domain&mdash;one that uses [!INCLUDE[prod_short](../includes/prod_short.md)] data and processes and maximizes your productivity. With Power Apps custom UI, AI builder, and augmented-reality (AR)/mixed-reality (MR) technologies, you can take your business to the next level with cutting-edge innovation and customized UI. 

For more information, see [Integrating with Microsoft Power Apps overview](../powerplatform/power-apps-overview.md)

## Connector: Integrating Business Central with Microsoft Power Automate

You can integrate [!INCLUDE[prod_short](../includes/prod_short.md)] with Microsoft Power Automate by using the [!INCLUDE[prod_short](../includes/prod_short.md)] connector for Power Platform. With Power Automate, you can set up and use flows to connect business-process tasks performed by different users. System tasks, such as automatic posting, can be included as steps in flows, preceded or followed by user tasks. Requesting and granting approval to create new records are typical flow steps.

For more information, see [Integrating with Microsoft Power Automate overview](../powerplatform/power-automate-overview.md)


## Integrating Business Central with Microsoft Power BI

You can integrate [!INCLUDE[prod_short](../includes/prod_short.md)] with Microsoft Power BI in two ways:

- Connect a Power BI semantic model to [!INCLUDE[prod_short](../includes/prod_short.md)] to read data.
- Embed a Power BI report, page, or visual in the [!INCLUDE[prod_short](../includes/prod_short.md)] client.

### Connector: How to connect a Power BI semantic model to Business Central to read data

[!INCLUDE[prod_short](../includes/prod_short.md)] integrates with Power BI through a connector using OData. The connector can read data from API pages/queries and from UI pages exposed as OData web services.

:::image type="content" source="/dynamics365/business-central/media/power-bi-architecture.svg" alt-text="Image alt text." lightbox="/dynamics365/business-central/media/power-bi-architecture.svg":::

For more information, see [Power BI integration overview](/dynamics365/business-central/admin-powerbi-overview).

### How to embed a Power BI report, page, or visual in the Business Central client

[!INCLUDE[prod_short](../includes/prod_short.md)] supports that a Power BI report, page, or visual can be embedded in the Business Central client by using an iframe. 

There are two ways that a Power BI report, page, or visual can be added to a page in the [!INCLUDE[prod_short](../includes/prod_short.md)] client:
1. A user can embed a Power BI report, page, or scorecard on pages that include a Power BI part. For more information, see [Working with Power BI Reports in Business Central](/dynamics365/business-central/across-working-with-powerbi).
1. A developer can programatically add them from AL. For more information, see [Adding Power BI Report parts to pages](../developer/devenv-power-bi-report-parts.md).

## Built-in: Integrating Business Central with Dataverse

[!INCLUDE[prod_short](../includes/prod_short.md)] has four built-in ways to integrate with [!INCLUDE[dataverse_short](../includes/dataverse_short.md)]: 

- Data synchronization that replicates data between [!INCLUDE[prod_short](../includes/prod_short.md)] and [!INCLUDE[dataverse_short](../includes/dataverse_short.md)].
- Data virtualization with virtual tables in [!INCLUDE[dataverse_short](../includes/dataverse_short.md)] via [!INCLUDE[prod_short](../includes/prod_short.md)] API for (**C**reate/**R**ead/**U**pdate/**D**elete) operations.
- Data change (**CUD**) events using webhooks.
- Business events (preview).

[![Shows the four interactions with Business Central](media/four-complementary-interactions.png)](media/four-complementary-interactions.png#lightbox)

For more information, see [Integrating Business Central with Microsoft Dataverse](dataverse-integration-overview.md).


## Built-in: Integrating Business Central with Microsoft Power Pages (preview)

You can integrate [!INCLUDE[prod_short](../includes/prod_short.md)] with Microsoft Power Pages by using virtual tables in Dataverse. With Power Pages, you can allow unlicensed external users to access data stored in [!INCLUDE[prod_short](../includes/prod_short.md)] online.

[![Shows how data virtualization works between Business Central and Dataverse](media/dataverse-virtual-tables.svg)](media/dataverse-virtual-tables.svg#lightbox)

For more information, see [Integrating with Microsoft Power Pages (preview)](../developer/power-pages-on-virtual-tables-overview.md).


## Built-in: Integrating Business Central with Dynamics 365 Sales

You can integrate [!INCLUDE[prod_short](../includes/prod_short.md)] with Dynamics 365 Sales by first setting up integration to [!INCLUDE[dataverse_short](../includes/dataverse_short.md)] and then do more setup from the [!INCLUDE[prod_short](../includes/prod_short.md)] application. Integrating to Dynamics 365 Sales lets users view information from [!INCLUDE[prod_short](../includes/prod_short.md)] while they're working in Dynamics 365 Sales. For example, when preparing a sales quote it could be useful to know whether you have enough inventory to fulfill the order.

For more information, see [Integrating Business Central with Dynamics 365 Sales](/dynamics365/business-central/admin-prepare-dynamics-365-for-sales-for-integration)  

## Built-in: Integrating Business Central with Shopify

You can integrate [!INCLUDE[prod_short](../includes/prod_short.md)] with Shopify by installing and configuring the Shopify Connector app. By connecting your Shopify store (or stores) with [!INCLUDE[prod_short](../includes/prod_short.md)], you can maximize your business productivity and manage and view insights from your business and your Shopify store as one unit.

For more information, see [Get started with the Shopify connector](/dynamics365/business-central/shopify/get-started).


## Built-in: Telemetry with Azure Application Insights

You can integrate [!INCLUDE[prod_short](../includes/prod_short.md)] with Azure Application Insights by enabling the telemetry feature. With telemetry, system owners can look at usage and lifecycle operations of environments/apps, diagnose problems, and analyze operations that affect performance.

:::image type="content" source="../developer/media/telemetry-architecture.svg" alt-text="Shows how Environment-level telemetry and App/extension-level telemetry works in Business Central AL" lightbox="../developer/media/telemetry-architecture.svg":::

For more information, see [Monitoring and Analyzing Telemetry in Azure Application Insights](../administration/telemetry-overview.md).


## Integrating to external systems from AL code: calling external services

You can integrate [!INCLUDE[prod_short](../includes/prod_short.md)] apps/extensions with external systems by using the *HttpClient* data type in AL code.

:::image type="content" source="media/httpclient.svg" alt-text="Shows how AL apps/extensions can call external web services from Business Central" lightbox="media/httpclient.svg":::

For more information, see [Integrating to external services with the HttpClient data type](../developer/devenv-httpclient.md).

## Integrating to external systems from AL code: Azure services

You can integrate [!INCLUDE[prod_short](../includes/prod_short.md)] apps/extensions with Azure services such as Azure Blob Services, Azure File Services, Azure Functions, or Azure Key Vault. 

:::image type="content" source="media/connect-to-azure-services.svg" alt-text="Shows how AL apps/extensions can call Azure services from Business Central" lightbox="media/connect-to-azure-services.svg":::

For more information, see [Integrating Business Central with Azure services](./azure-integration-overview.md).

## Integrating to external systems from AL code: copilot

You can integrate [!INCLUDE[prod_short](../includes/prod_short.md)] apps/extensions with the Azure Open AI Service to include copilot and generative AI experiences. 

![Shows the tasks in the generative-AI development](media/dev-generative-ai-overview.svg)

For more information, see [Integrating AI using Developer Tools for Copilot](../developer/ai-integration-landing-page.yml).


## Integrating to external systems from AL code: Microsoft Teams

You can integrate [!INCLUDE[prod_short](../includes/prod_short.md)] apps/extensions with Microsoft Teams. [!INCLUDE [prod_short](../includes/prod_short.md)] offers an app that connects Microsoft Teams to the data in [!INCLUDE [prod_short](../includes/prod_short.md)] so that users can quickly share details across team members and respond faster to inquiries. 

[![Teams integration with Business Central.](media/teams-intro-v3.png)](media/teams-intro-v3.png#lightbox)

For more information, see [Integrating with Microsoft Teams overview](../developer/devenv-develop-for-teams.md).

## See also

[Web services overview](../webservices/web-services.md)  
[Developing Connect apps](../developer/devenv-develop-connect-apps.md)   
[Business Central connector for Power Platform](/connectors/dynamicssmbsaas)   
[Integrating with Microsoft Power Apps overview](../powerplatform/power-apps-overview.md)  
[Integrating with Microsoft Power Automate overview](../powerplatform/power-automate-overview.md)  
[Integrating with Microsoft Power Pages (preview)](../developer/power-pages-on-virtual-tables-overview.md)  
[Integrating with Microsoft Power BI](/dynamics365/business-central/admin-powerbi-overview)  
[How users can embed Power BI Reports in Business Central](/dynamics365/business-central/across-working-with-powerbi)  
[How AL developers can add Power BI Reports to pages](../developer/devenv-power-bi-report-parts.md)  
[Integrating Business Central with Microsoft Dataverse](dataverse-integration-overview.md)  
[Integrating Business Central with Dynamics 365 Sales](/dynamics365/business-central/admin-prepare-dynamics-365-for-sales-for-integration)  
[Integrating Business Central with Shopify](/dynamics365/business-central/shopify/get-started)  
[Integrating Business Central with Azure Application Insights](../administration/telemetry-overview.md)
[Integrating to external services from AL using the HttpClient data type](../developer/devenv-httpclient.md)  
[Integrating Business Central with Azure services](./azure-integration-overview.md)
[Integrating AI using Developer Tools for Copilot](../developer/ai-integration-landing-page.yml)
[Integrating Business Central with Azure services](./azure-integration-overview.md)
[Integrating with Microsoft Teams overview](../developer/devenv-develop-for-teams.md)  