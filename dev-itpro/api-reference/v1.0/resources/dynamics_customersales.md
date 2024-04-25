---
title: (v1.0) customerSales resource type
description: (v1.0) A customer sales in Dynamics 365 Business Central.
 
author: SusanneWindfeldPedersen

ms.topic: reference
ms.devlang: al
ms.date: 04/01/2019
ms.author: solsen
---

# customerSales resource type (v1.0)

[!INCLUDE[d365_api_newversion](../../../includes/d365_api_newversion.md)]

Represents an customer sales in [!INCLUDE[prod_short](../../../includes/prod_short.md)].

> [!NOTE]  
> For information about enabling APIs for [!INCLUDE[prod_short](../../../includes/prod_short.md)] see [Enabling the APIs for Dynamics 365 Business Central](../enabling-apis-for-dynamics-nav.md).

## Methods

| Method            | Return Type |Description               |
|:------------------|:------------|:-------------------------|
|[GET customerSales](../api/dynamics_customerSales_get.md)|CustomerSales|Get a customer sales object|

## Properties

| Property            | Type  |Description                                       |
|:--------------------|:------|:-------------------------------------------------|
|customerId           |GUID   |Represents the customer ID.                       |
|customerNumber       |string |Represents the customer number.                   |
|name                 |string |Represents the name of the customer.              |
|totalSalesAmount     |numeric|Represents the customer sales.                    |
|dateFilter_FilterOnly|date   |Represents the date filter for the customer sales.|


## Relationships
None

## JSON representation

Here is a JSON representation of the resource.


```json
{
    "customerId": "GUID",
    "customerNumber": "string",
    "name": "string",
    "totalSalesAmount": "decimal",
    "dateFilter_FilterOnly": "date"
}
```
## See also
  
[Get Customer Sales](../api/dynamics_customersales_get.md)  
