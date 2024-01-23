---
title: (v1.0) customerPaymentsJournals resource type
description: (v1.0) A customer payments journal in Dynamics 365 Business Central.
 
author: SusanneWindfeldPedersen

ms.topic: reference
ms.devlang: al
ms.date: 04/01/2019
ms.author: solsen
---

# customerPaymentsJournals resource type (v1.0)

[!INCLUDE[d365_api_newversion](../../../includes/d365_api_newversion.md)]

Represents a customer payments journal in [!INCLUDE[prod_short](../../../includes/prod_short.md)].

> [!NOTE]  
> For information about enabling APIs for [!INCLUDE[prod_short](../../../includes/prod_short.md)] see [Enabling the APIs for Dynamics 365 Business Central](../enabling-apis-for-dynamics-nav.md).

## Methods

| Method               | Return Type             |Description                      |
|:---------------------|:------------------------|:--------------------------------|
|[GET customerPaymentsJournals](../api/dynamics_customerpaymentsjournal_get.md)      |customerPaymentsJournals|Gets a customer payments journal.   |
|[POST customerPaymentsJournals](../api/dynamics_create_customerpaymentsjournal.md)  |customerPaymentsJournals|Creates a customer payments journal.|
|[PATCH customerPaymentsJournals](../api/dynamics_customerpaymentsjournal_update.md) |customerPaymentsJournals|Updates a customer payments journal.|
|[DELETE customerPaymentsJournals](../api/dynamics_customerpaymentsjournal_delete.md)|none                     |Deletes a customer payments journal.|

## Properties

| Property           | Type                  |Description                                                             |
|:-------------------|:----------------------|:-----------------------------------------------------------------------|
|id                  |GUID                   |The unique ID of the customer payments journal. Non-editable.           |
|code                |string, maximum size 10| The code of the customer payments journal.                             |
|displayName         |string, maximum size 50| The display name of the customer payments journal.                     |
|lastModifiedDateTime|datetime               |The last datetime the customer payments journal was modified. Read-Only.|

## Relationships

## JSON representation

Here is a JSON representation of the resource.


```json
{
  "id": "GUID",
  "code": "String",
  "displayName": "String",
  "lastModifiedDateTime": "datetime"
}
```

## See also
[Microsoft Graph Reference](../api/dynamics_graph_reference.md)  
  
[Customer Payments Journal](../api/dynamics_customerpaymentsjournal_get.md)  
[Post Customer Payments Journal](../api/dynamics_create_customerpaymentsjournal.md)  
[Patch Customer Payments Journal](../api/dynamics_customerpaymentsjournal_update.md)  
[Delete Customer Payments Journal](../api/dynamics_customerpaymentsjournal_delete.md)  
