---
title: (v1.0) irs1099Codes resource type
description: (v1.0) An IRS 1099 Code object in Dynamics 365 Business Central.
 
author: SusanneWindfeldPedersen

ms.topic: reference
ms.devlang: al
ms.date: 04/01/2019
ms.author: solsen
---

# irs1099Codes resource type (v1.0)

[!INCLUDE[d365_api_newversion](../../../includes/d365_api_newversion.md)]

Represents an irs1099Codes object in [!INCLUDE[prod_short](../../../includes/prod_short.md)]. IRS 1099 codes are used for reporting to the IRS.

> [!NOTE]  
> For information about enabling APIs for [!INCLUDE[prod_short](../../../includes/prod_short.md)] see [Enabling the APIs for Dynamics 365 Business Central](../enabling-apis-for-dynamics-nav.md).

## Methods

| Method                                                 | Return Type|Description            |
|:-------------------------------------------------------|:-----------|:----------------------|
|[GET irs1099Codes](../api/dynamics_irs1099_get.md)      |irs1099Codes|Gets an IRS 1099 code. |
|[POST irs1099Codes](../api/dynamics_create_irs1099.md)  |irs1099Codes|Creates an IRS 1099 code.|
|[PATCH irs1099Codes](../api/dynamics_irs1099_update.md) |irs1099Codes|Update an IRS 1099 code.|
|[DELETE irs1099Codes](../api/dynamics_irs1099_delete.md)|none        |Delete an IRS 1099 code.|

## Properties

| Property           | Type     |Description                                      |
|:-------------------|:-------|:------------------------------------------------|
|id                  |GUID    |The unique ID of the IRS 1099 Code. Non-editable.|
|code                |string  |Specifies the IRS 1099 Code.                     |
|displayName         |string  |Specifies the IRS 1099 Code display name.        |
|minimumReportable   |decimal |Specifies the minimum value for this box that must be reported to the IRS on a 1099 form.|
|lastModifiedDateTime|datetime|The last datetime the IRS 1099 Code was modified. Read-Only.|  


## Relationships
None

## JSON representation

Here is a JSON representation of the irs1099Codes.


```json
{
  "id": "GUID",
  "code": "string",
  "displayName": "string",
  "minimumReportable": "decimal",
  "lastModifiedDateTime": "datetime"
}
```

## See also

[Get IRS 1099](../api/dynamics_irs1099_get.md)  
[Post IRS 1099](../api/dynamics_create_irs1099.md)  
[Patch IRS 1099](../api/dynamics_irs1099_update.md)  
[Delete IRS 1099](../api/dynamics_irs1099_delete.md)  