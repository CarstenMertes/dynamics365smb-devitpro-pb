---
title: countryRegion resource type  
description: A country/region object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/01/2021
ms.author: solsen
---

# countryRegion resource type

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

<!-- START>DO_NOT_EDIT -->
<!-- IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT. -->
Represents a country/region in [!INCLUDE[prod_short](../../../includes/prod_short.md)].

> [!NOTE]
> For information about enabling APIs for [!INCLUDE[prod_short](../../../includes/prod_short.md)] see [Enabling the APIs for Dynamics 365 Business Central](../enabling-apis-for-dynamics-nav.md).

## Methods

| Method | Return Type|Description |
|:--------------------|:-----------|:-------------------------|
|[GET countryRegion](../api/dynamics_countryregion_get.md)|countryRegion|Gets a country/region object.|
|[DELETE countryRegion](../api/dynamics_countryregion_delete.md)|none|Deletes a country/region object.|
|[POST countryRegion](../api/dynamics_countryregion_create.md)|countryRegion|Creates a country/region object.|
|[PATCH countryRegion](../api/dynamics_countryregion_update.md)|countryRegion|Updates a country/region object.|



## Properties

| Property           | Type   |Description     |
|:-------------------|:-------|:---------------|
|id|GUID|The unique ID of the country/region. Non-editable.|
|code|string|The code of the country/region.|
|displayName|string|Specifies the country/region's name. This name will appear on all sales documents for the country/region.|
|addressFormat|NAV.countryRegionAddressFormat|Specifies the format of the address that is displayed on external-facing documents. You link an address format to a country/region code so that external-facing documents based on cards or documents with that country/region code use the specified address format.|
|lastModifiedDateTime|datetime|The last datetime the country/region was modified. Read-Only.|

## JSON representation

Here is a JSON representation of the countryRegion resource.


```json
{
    "id": "GUID",
    "code": "string",
    "displayName": "string",
    "addressFormat": "NAV.countryRegionAddressFormat",
    "lastModifiedDateTime": "datetime"
}
```
<!-- IMPORTANT: END>DO_NOT_EDIT -->



## See Also
[GET countryRegion](../api/dynamics_countryRegion_Get.md)  
[DELETE countryRegion](../api/dynamics_countryRegion_Delete.md)  
[POST countryRegion](../api/dynamics_countryRegion_Create.md)  
[PATCH countryRegion](../api/dynamics_countryRegion_Update.md)
