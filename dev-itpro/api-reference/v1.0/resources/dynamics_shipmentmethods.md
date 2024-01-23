---
title: (v1.0) shipmentMethods resource type
description: (v1.0) A shipment method in Dynamics 365 Business Central. 
 
author: SusanneWindfeldPedersen

ms.topic: reference
ms.devlang: al
ms.date: 04/01/2019
ms.author: solsen
---

# shipmentMethods resource type (v1.0)

[!INCLUDE[d365_api_newversion](../../../includes/d365_api_newversion.md)]

Represents a method of shipment in [!INCLUDE[prod_short](../../../includes/prod_short.md)], such as UPS, Fedex, and DHL.

> [!NOTE]  
> For information about enabling APIs for [!INCLUDE[prod_short](../../../includes/prod_short.md)] see [Enabling the APIs for Dynamics 365 Business Central](../enabling-apis-for-dynamics-nav.md).

## Methods

| Method       | Return Type  |Description|
|:---------------|:--------|:----------|
|[GET shipmentMethods](../api/dynamics_shipmentmethods_get.md)|shipmentMethods|Gets a shipment method.|
|[POST shipmentMethods](../api/dynamics_create_shipmentmethods.md)|shipmentMethods|Creates a shipment method.|
|[PATCH shipmentMethods](../api/dynamics_shipmentmethods_update.md)|shipmentMethods|Updates a shipment method.|
|[DELETE shipmentMethods](../api/dynamics_shipmentmethods_delete.md)|none|Deletes a shipment method.|

## Properties

| Property     | Type   |Description|
|:---------------|:--------|:----------|
|id|GUID|The unique ID of the shipmentMethod. Non-editable.|
|code|string|Specifies the shipment method code.|
|displayName|string|Specifies the shipment method display name.|
|lastModifiedDateTime|datetime|The last datetime the shipment method was modified. Read-Only.|  


## Relationships
None

## JSON representation

Here is a JSON representation of the shipmentMethod.

```json
{
  "id": "GUID",
  "code": "string",
  "displayName": "string",
  "lastModifiedDateTime": "datetime"
}
```

## See also

[Get Shipment Methods](../api/dynamics_shipmentmethods_get.md)  
[Create Shipment Methods](../api/dynamics_create_shipmentmethods.md)  
[Update Shipment Methods](../api/dynamics_shipmentmethods_update.md)  
[Delete Shipment Methods](../api/dynamics_shipmentmethods_delete.md)  
