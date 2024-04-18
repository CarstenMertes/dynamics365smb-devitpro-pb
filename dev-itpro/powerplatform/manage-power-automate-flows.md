---
title: Manage Power Automate Flows
description: Learn to manage Power Automate flows for Business Central online.
author: jswymer
ms.custom: na
ms.topic: 
ms.date: 05/23/2023
ms.author: jswymer
---

# Manage existing Power Automate flows for Business Central

Managing existing flows (like editing the flow steps or turning them on or off) is done directly in Power Automate. You can get to your flows in Power Automate in two ways:

- Sign in to [Power Automate](https://powerautomate.com), then select **My flows** from the navigation bar on the left.
- From Business Central,  open a list, card, or document page, select **Automate** > **Manage Flows**.

On the **My flows** page, you can find any flows you have already created and those shared with you by an admin or coworker.

## View details and edit flow in Power Automate

To view details about a flow from the **My flows** page in Power Automate, select the vertical ellipsis (⋮) for your flow, and then select **Details**. The details page includes the following information: 

| Name | Description |
| ----------- | ----------- |
| Details | Shows details about the flow such as when it was created and modified, the current status, flow type, and the owner of the flow. |
| Connections | Shows the connections being used by the flow, such as data sources and applications. |
| Owners | Shows who owns the flow. You can add more owners by choosing this option. Learn more at [Share a cloud flow](/power-automate/create-team-flows) |
| Process insights (preview) | Shows the average time your flow takes to complete. It also identifies possible bottlenecks, which could streamline your flow if you fix them. |
| 28-day run history | Shows the run history of your flow for past 28 days including start date, duration of the flow, and the current status.  |
| Run-only users | Shows the users with whom you've shared your flow and have permission to run it.  |

> [!TIP]
> Because *run-only* includes limited access, you can add other users or groups as owners so they can edit and update the flow. Just select **Edit** in the *Connections* pane.

To edit a flow, select the vertical ellipsis (⋮) for your flow, and then select **Edit**.

For more information about working with flows in Power Automates, explore [Power Automate documentation](/power-automate/).

## Use the Manage Power Automate Flows page in Business Central

> **APPLIES TO:** [!INCLUDE[prod_short](../includes/prod_short.md)] online version 21 and earlier. The **Manage Power Automate Flows** page has been deprecated in version 22 and replaced by actions in the **Automate** actions group on pages.

You can either create new flows or manage the existing Power Automate flows from [!INCLUDE[prod_short](../includes/prod_short.md)] from the **Manage Power Automate Flows** page. To check out that page, go to the *search* icon in the top right and enter *manage power automate flows.* The resulting page presents various ways to look for details and manage your created flows. In addition, you can create a new flow, edit it, share it, make a copy, delete, or run other commands on your flows by selecting them from the list. Here are the categories of flows you find on the main page: 

| Category | Description |
| ----------- | ----------- |
| Cloud flows | This category shows a list of flows you've created using Power Automate. Flows can be either flow type [Instant](instant-flows.md) or [Automated](automate-workflows.md).  |
| Desktop flows | This category shows a list of flows you've created for your desktop environment using Power Automate. If you haven't created any, you can create one by choosing **+ New desktop flow**. Learn more at [Desktop Flows](/power-automate/desktop-flows/create-flow). |
| Shared with me | This category shows a list of flows shared with you by other users in your organization. |

You can also create flows by choosing **+ New flow** on the **Manage Power Automate Flows** page. Then choose the flow type you want to create from among the types in the drop-down list:

- Template
- Automated cloud flow
- Instant cloud flow
- Scheduled cloud flow
- Desktop flow
- Business process flow

### Other settings

You can find two more menu items on the **Manage Power Automate** flows page: **Home** and **Configuration**. 

- Choose **Home** to open *Power Automate* or find *flow entries*.
- Choose **Configuration** to select the environment in which you want to create or see the flows.

You can also find the connection information for the [!INCLUDE[prod_short](../includes/prod_short.md)] connector for Power Automate under **Configuration**.

> [!NOTE]
> **Flow entries** shows the list of records upon which the flow is acting. Such as a record of a user to whom the flow sent an approval request, indicating the request status and other details of the record. 

## See also

[Set up Automated Flows](automate-workflows.md)  
[Set up Instant Flows](instant-flows.md)  
[Troubleshoot Your Business Central Automated Workflows](/dynamics365/business-central/across-flow-troubleshoot)  
