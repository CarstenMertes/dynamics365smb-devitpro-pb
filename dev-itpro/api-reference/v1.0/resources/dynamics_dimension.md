---
title: (v1.0) dimensions resource type
description: (v1.0) A dimension in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen

ms.topic: reference
ms.devlang: al
ms.date: 04/01/2019
ms.author: solsen
---

# Dimensions resource type (v1.0)

[!INCLUDE[d365_api_newversion](../../../includes/d365_api_newversion.md)]

Represents a dimension in [!INCLUDE[prod_short](../../../includes/prod_short.md)].

> [!NOTE]  
> For information about enabling APIs for [!INCLUDE[prod_short](../../../includes/prod_short.md)] see [Enabling the APIs for Dynamics 365 Business Central](../enabling-apis-for-dynamics-nav.md).

## Methods

| Method       | Return Type  |Description|
|:-------------|:-------------|:----------|
|[GET dimensions](../api/dynamics_dimension_get.md)|dimension|Gets a dimension.|


## Properties

| Property           | Type                  |Description               |
|:-------------------|:----------------------|:-------------------------|
|id                  |GUID                   |The unique ID of the item.|
|code                |string, maximum size 20|The dimension code.       |
|displayName         |string                 |Specifies the dimension's name. This name will appear where the dimension is used.|
|lastModifiedDateTime|datetime               |The last datetime the dimension was modified.|  


## JSON representation

Here is a JSON representation of the resource.


```json
{

    "id": "GUID",
    "code": "string",
    "displayName": "string",
    "lastModifiedDateTime": "datetime"
}
```


## See also
  
[Get Dimensions](../api/dynamics_dimension_get.md)  