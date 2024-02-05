---
title: Power Automate Integration overview
description: This article provides an overview of how Power Automate and Business Central integrate. 
author: jswymer
ms.author: jswymer
ms.reviewer: jswymer

ms.topic: overview
ms.date: 09/27/2023
ms.custom: bap-template
---
# Power Automate integration overview

[!INCLUDE [online_only](../developer/includes/online_only.md)]

[Power Automate](/power-automate/) is a no code/low code solution to create business workflows in the context of [!INCLUDE[prod_short](../includes/prod_short.md)]. Use it to connect to cloud services, like the following, and create flows that use multiple data sources.

- Dataverse  
- Outlook  
- Teams  
- Approvals  
- Excel  
- SharePoint  
- Connectors to partner services 

With Power Automate, you can set up and use flows to connect business-process tasks performed by different users. System tasks, such as automatic posting, can be included as steps in flows, preceded or followed by user tasks. Requesting and granting approval to create new records are typical flow steps. Learn more about Power Automate in the [Power Automate Documentation](/power-automate/getting-started).

## About Power Automate flows with Business Central

The two types of Power Automate flows that you can use with Business Central are:

- **Automated flows**

  Automated flows are triggered by events (such as record or document creation, modification, or deletion) or run automatically on a user-defined schedule. You create automated flows in Power Automate, which you can access by going directly to the Power Automate home page or from Business Central. For more information, see [Set Up Automated Flows](automate-workflows.md).

- **Instant flows**

    In Business Central, users can manually trigger instant flows instead of using events to automatically trigger them. Instant flows show in the **Automate** action group in the Business Central client so users can run the flows in context of their work. You create and trigger a Power Automate instant flow on a Business Central record, such as a customer, item, or sales order, with options to manipulate information both internally and externally (using integrated tools). For more information, see [Set Up Instant Flows](instant-flows.md).

In addition to Power Automate flow, Business Central also offers approval workflow templates as a separate workflow system. However, any workflow template you create with Power Automate is added to the list of workflows within Business Central. Learn more at [Workflows in Dynamics 365 Business Central](/dynamics365/business-central/across-workflow).

## The Business Central connector

A *connector* is a proxy or a wrapper around an API that allows the underlying service to talk to Microsoft Power Automate. For communicating with Power Automate, Business Central has its own connector. When you create flows that interact with Business Central, you build the flows using the Business Central connector. To create flows, you don't necessarily need to know the details about the connector and its API, but it helps in some cases. To learn more about connectors and the Business Central connector API, see [Connectors Overview](/connectors/connectors) and [Dynamics 365 Business Central](/connectors/dynamicssmbsaas) in the Power Platform documentation.

The Dynamics 365 Business Central includes several *triggers* and *actions* for building flows. Triggers are events in Business Central that start a flow, like when a record is created or deleted. Starting in 2023 release wave 2, the connector also supports starting flows based on a [business event](../developer/business-events-overview.md) via the [When a business event occurs (V3)](/connectors/dynamicssmbsaas/#when-a-business-event-occurs-(v3)-(preview)) trigger. Actions run an operation after a trigger, like getting a record.

Business Central connector can also initiate actions provided through other connectors. For example, sending an email using Office 365 connector or starting a chat in Teams using the Microsoft Teams connector.

> [!NOTE]
> The connector currently doesn't support service-to-service (S2S) authentication.  This also applies to Power Automate, Azure Logic Apps, and Power Apps. Partners interested in such scenarios must for now rely on the OData connector.

## What users can do from inside Business Central

With Power Automate integration, users can create and run Power Automate instant flows directly from the most list, card, and document pages. These pages have an **Automate** action group in the action bar, which includes actions for creating and managing flows, and also running existing flows created or shared in Power Automate.

:::image type="content" source="../developer/media/power-automate-menu.svg" alt-text="Shows the Automate action in the action bar with expanded actions.":::

For more information, see [Use Power Automate Flows in Business Central](/dynamics365/business-central/across-how-use-financials-data-source-flow#run-instant-flows) in the business functionality help.

## What AL developers can do in extensions

In AL, developers can define page actions that trigger a Power Automate flow using custom actions. Custom actions are defined next to other actions but use the `customaction` AL keyword instead. In the UI, they can be placed everywhere other actions can. Learn more at [Actions Overview](../developer/devenv-actions-overview.md#run-power-automate-flows-from-page-actions).

## Next steps

The next step is to set up Power Automate integration in Business Central. By default, all users have access to the Power Automate features in the client. As an admin, you can choose to turn off the ability, either for the entire organization or for individual users. Learn more at [Set Up Power Automate](power-automate-setup.md).
