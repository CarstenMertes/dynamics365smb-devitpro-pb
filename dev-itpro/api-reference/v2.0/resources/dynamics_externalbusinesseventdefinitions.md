---
title: externalBusinessEventDefinitions resource type
description: Represents external business event definitions that describe available business events for integration with Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/08/2026
ms.author: solsen
ms.reviewer: solsen
---

# externalBusinessEventDefinitions resource type

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Represents an external business event definition in [!INCLUDE[prod_short](../../../includes/prod_short.md)]. External business event definitions describe the business events that are available for external consumers to subscribe to.

> [!NOTE]
> For information about enabling APIs for [!INCLUDE[prod_short](../../../includes/prod_short.md)] see [Enabling the APIs for Dynamics 365 Business Central](../enabling-apis-for-dynamics-nav.md).

## Methods

| Method | Return Type|Description |
|:--------------------|:-----------|:-------------------------|
|[GET externalBusinessEventDefinitions](../api/dynamics_externalbusinesseventdefinitions_get.md)|externalBusinessEventDefinitions|Gets an external business event definition object.|

## Properties

| Property           | Type   |Description     |
|:-------------------|:-------|:---------------|
|appId|GUID|The ID of the app that defines the business event.|
|name|string|The name of the business event.|
|eventVersion|string|The version of the business event.|
|payload|string|The payload schema of the business event.|
|displayName|string|The display name of the business event.|
|description|string|The description of the business event.|
|category|string|The category of the business event.|
|appName|string|The name of the app that defines the business event.|
|appPublisher|string|The publisher of the app that defines the business event.|
|appVersion|string|The version of the app that defines the business event.|

## JSON representation

Here's a JSON representation of the externalBusinessEventDefinitions resource.

```json
{
    "appId": "00000000-0000-0000-0000-000000000000",
    "name": "SalesOrderPosted",
    "eventVersion": "1.0",
    "payload": "string",
    "displayName": "Sales order posted",
    "description": "Triggered when a sales order is posted.",
    "category": "Sales",
    "appName": "Base Application",
    "appPublisher": "Microsoft",
    "appVersion": "25.0.0.0"
}
```

## Related information

[GET externalBusinessEventDefinitions](../api/dynamics_externalbusinesseventdefinitions_get.md)
