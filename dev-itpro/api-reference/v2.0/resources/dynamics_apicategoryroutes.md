---
title: apiCategoryRoutes resource type
description: Represents API category routes that describe available API publishers, groups, and versions in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/08/2026
ms.author: solsen
ms.reviewer: solsen
---

# apiCategoryRoutes resource type

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Represents an API category route in [!INCLUDE[prod_short](../../../includes/prod_short.md)]. API category routes describe the available API publishers, groups, and versions.

> [!NOTE]
> For information about enabling APIs for [!INCLUDE[prod_short](../../../includes/prod_short.md)] see [Enabling the APIs for Dynamics 365 Business Central](../enabling-apis-for-dynamics-nav.md).

## Methods

| Method | Return Type|Description |
|:--------------------|:-----------|:-------------------------|
|[GET apiCategoryRoutes](../api/dynamics_apicategoryroutes_get.md)|apiCategoryRoutes|Gets an API category route object.|

## Properties

| Property           | Type   |Description     |
|:-------------------|:-------|:---------------|
|route|string|The full route path of the API category.|
|publisher|string|The publisher of the API.|
|group|string|The API group name.|
|version|string|The API version.|

## JSON representation

Here's a JSON representation of the apiCategoryRoutes resource.

```json
{
    "route": "microsoft/api/v2.0",
    "publisher": "microsoft",
    "group": "api",
    "version": "v2.0"
}
```

## Related information

[GET apiCategoryRoutes](../api/dynamics_apicategoryroutes_get.md)
