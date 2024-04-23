---
title: (v1.0) taxGroups resource type
description: (v1.0) A tax group object in Dynamics 365 Business Central. 
 
author: SusanneWindfeldPedersen

ms.topic: reference
ms.devlang: al
ms.date: 04/01/2019
ms.author: solsen
---

# taxGroups resource type (v1.0)

[!INCLUDE[d365_api_newversion](../../../includes/d365_api_newversion.md)]

Represents a taxGroups resource type in [!INCLUDE[prod_short](../../../includes/prod_short.md)].

> [!NOTE]  
> For information about enabling APIs for [!INCLUDE[prod_short](../../../includes/prod_short.md)] see [Enabling the APIs for Dynamics 365 Business Central](../enabling-apis-for-dynamics-nav.md).

## Methods

| Method       | Return Type  |Description|
|:---------------|:--------|:----------|
|[GET taxGroups](../api/dynamics_taxGroups_get.md)|taxGroups|Gets a tax group object.|
|[POST taxGroups](../api/dynamics_create_taxGroups.md)|taxGroups|Creates a tax group object.|
|[PATCH taxGroups](../api/dynamics_taxGroups_update.md)|taxGroups|Updates a tax group object.|
|[DELETE taxGroups](../api/dynamics_taxGroups_delete.md)|none|Deletes a tax group object.|

## Properties

| Property     | Type   |Description|
|:---------------|:--------|:----------|
|id|GUID|The unique ID of the taxGroup. Read-Only.|
|code|string|Specifies the tax group.|
|displayName|string|Specifies the tax group display name.|
|lastModifiedDateTime|datetime|The last datetime the tax group was modified. Read-Only.|  


## Relationships
None

## JSON representation

Here is a JSON representation of the taxGroup.

```json
{
  "id": "GUID",
  "code": "string",
  "displayName": "string",
  "lastModifiedDateTime": "datetime"
}
```

## See Also

[Get Tax Groups](../api/dynamics_taxgroups_get.md)  
[Create Tax Groups](../api/dynamics_create_taxgroups.md)  
[Update Tax Groups](../api/dynamics_taxgroups_update.md)  
[Delete Tax Groups](../api/dynamics_taxgroups_delete.md)  