---
title: tableMapping resource type
description: A table mapping object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 03/25/2022
ms.author: solsen
---

# tableMapping resource type

<!-- START>DO_NOT_EDIT -->
<!-- IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT. -->
Represents a table mapping in [!INCLUDE[prod_short](../../../includes/prod_short.md)] that can be used to include custom tables or tables that are not included in the cloud migration out of the box. If you provide a table mapping the source table will be copied to the destination table during cloud migration.

> [!NOTE]
> For information about enabling APIs for [!INCLUDE[prod_short](../../../includes/prod_short.md)] see [guideline](../../../api-reference/v2.0/endpoints-apis-for-dynamics.md).

## Methods

| Method | Return Type|Description |
|:--------------------|:-----------|:-------------------------|
|[GET tableMapping](../api/dynamics_tablemapping_get.md)|tableMapping|Gets a table mapping object.|
|[DELETE tableMapping](../api/dynamics_tablemapping_delete.md)|none|Deletes a table mapping object.|
|[POST tableMapping](../api/dynamics_tablemapping_create.md)|tableMapping|Creates a table mapping object.|
|[PATCH tableMapping](../api/dynamics_tablemapping_update.md)|tableMapping|Updates a table mapping object.|

## Bound Actions

The tableMapping resource type offers a bound action called `deleteAllForExtension` which delete all for extensions the corresponding tableMapping batch.
This is illustrated in the following example:
`DELETEALLFOREXTENSION https://<server address>:<server API port>/<server instance name>/api/v1.0/companies({id})/tableMappings({id})/Microsoft.NAV.deleteAllForExtension`

The response has no content; the response code is 204.

The tableMapping resource type offers a bound action called `restoreDefaults` which restore defaultss the corresponding tableMapping batch.
This is illustrated in the following example:
`RESTOREDEFAULTS https://<server address>:<server API port>/<server instance name>/api/v1.0/companies({id})/tableMappings({id})/Microsoft.NAV.restoreDefaults`

The response has no content; the response code is 204.


## Properties

| Property           | Type   |Description     |
|:-------------------|:-------|:---------------|
|id|GUID|The unique ID of the table mapping. Non-editable.|
|tableId|integer|Specifies the destination table ID to be mapped.|
|tableName|string|Specifies the destination table name.|
|sourceTableName|string|Specifies the source table name.|
|extensionName|string|Specifies the extension name that owns the mapped table.|
|estimatedSize|decimal|Read-Only property representing the approximate size of the On-Prem company. The data migrated will be smaller, since the data will be compressed and not all tables will be included.|
|created|boolean|Specifies if the company was created. It will not reflect if the setup of the company was correct or not. For this you should check the status property. If the company has been created, however status is different.|


## JSON representation

Here is a JSON representation of the tableMapping resource.


```json
{
    "id": "GUID",
    "tableId": "integer",
    "tableName": "string",
    "sourceTableName": "string",
    "extensionName": "string"
}
```
<!-- IMPORTANT: END>DO_NOT_EDIT -->

## See Also
[GET tableMapping](../api/dynamics_tablemapping_get.md)  
[DELETE tableMapping](../api/dynamics_tablemapping_delete.md)  
[POST tableMapping](../api/dynamics_tablemapping_create.md)  
[PATCH tableMapping](../api/dynamics_tablemapping_update.md)
