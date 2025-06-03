---
title: customerReturnReason resource type
description: A customer return reason object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/28/2025
ms.author: solsen
ms.reviewer: solsen
---

# customerReturnReason resource type

Represents a customer return reason in [!INCLUDE[prod_short](../../../includes/prod_short.md)].

> [!NOTE]
> For information about enabling APIs for [!INCLUDE[prod_short](../../../includes/prod_short.md)] see [Enabling the APIs for Dynamics 365 Business Central](../enabling-apis-for-dynamics-nav.md).

## Methods

| Method | Return Type|Description |
|:--------------------|:-----------|:-------------------------|
|[GET customerReturnReason](../api/dynamics_customerreturnreason_get.md)|customerReturnReason|Gets a customer return reason object.|
|[DELETE customerReturnReason](../api/dynamics_customerreturnreason_delete.md)|none|Deletes a customer return reason object.|
|[POST customerReturnReason](../api/dynamics_customerreturnreason_create.md)|customerReturnReason|Creates a customer return reason object.|
|[PATCH customerReturnReason](../api/dynamics_customerreturnreason_update.md)|customerReturnReason|Updates a customer return reason object.|

## Properties

| Property           | Type   |Description     |
|:-------------------|:-------|:---------------|
|id|GUID|The unique ID of the customer return reason. Non-editable.|
|code|string|The code of the customer return reason.|
|description|string|Specifies the description of the customer return reason.|
|lastModifiedDateTime|datetime|The last datetime the customer return reason was modified. Read-Only.|

## JSON representation

Here's a JSON representation of the customerReturnReason resource.


```json
{
    "id": "GUID",
    "code": "string",
    "description": "string",
    "lastModifiedDateTime": "datetime"
}
```

## Related information

[GET customerReturnReason](../api/dynamics_customerreturnreason_get.md)   
[DELETE customerReturnReason](../api/dynamics_customerreturnreason_delete.md)  
[POST customerReturnReason](../api/dynamics_customerreturnreason_create.md)  
[PATCH customerReturnReason](../api/dynamics_customerreturnreason_update.md)  
