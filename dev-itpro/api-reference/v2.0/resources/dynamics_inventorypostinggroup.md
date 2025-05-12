---
title: inventoryPostingGroup resource type
description: An inventory posting group object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/28/2025
ms.author: solsen
ms.reviewer: solsen
---

# inventoryPostingGroup resource type

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Represents an inventory posting group in [!INCLUDE[prod_short](../../../includes/prod_short.md)].

> [!NOTE]
> For information about enabling APIs for [!INCLUDE[prod_short](../../../includes/prod_short.md)] see [Enabling the APIs for Dynamics 365 Business Central](../enabling-apis-for-dynamics-nav.md).

## Methods

| Method | Return Type|Description |
|:--------------------|:-----------|:-------------------------|
|[GET inventoryPostingGroup](../api/dynamics_inventorypostinggroup_get.md)|inventoryPostingGroup|Gets a inventory posting group object.|

## Properties

| Property           | Type   |Description     |
|:-------------------|:-------|:---------------|
|id|GUID|The unique ID of the inventory posting group. Non-editable.|
|code|string|The code of the inventory posting group.|
|description|string|Specifies the description of the inventory posting group.|
|lastModifiedDateTime|datetime|The last datetime the inventory posting group was modified. Read-Only.|

## JSON representation

Here's a JSON representation of the inventoryPostingGroup resource.

```json
{
    "id": "GUID",
    "code": "string",
    "description": "string",
    "lastModifiedDateTime": "datetime"
}
```

## Related information

[GET inventoryPostingGroup](../api/dynamics_inventorypostinggroup_get.md)
