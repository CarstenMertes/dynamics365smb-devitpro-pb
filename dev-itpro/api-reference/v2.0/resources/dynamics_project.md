---
title: project resource type  
description: A project object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/01/2021
ms.author: solsen
---

# project resource type

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

<!-- START>DO_NOT_EDIT -->
<!-- IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT. -->
Represents a project in [!INCLUDE[prod_short](../../../includes/prod_short.md)].

> [!NOTE]
> For information about enabling APIs for [!INCLUDE[prod_short](../../../includes/prod_short.md)] see [Enabling the APIs for Dynamics 365 Business Central](../enabling-apis-for-dynamics-nav.md).

## Methods

| Method | Return Type|Description |
|:--------------------|:-----------|:-------------------------|
|[GET project](../api/dynamics_project_get.md)|project|Gets a project object.|
|[DELETE project](../api/dynamics_project_delete.md)|none|Deletes a project object.|
|[POST project](../api/dynamics_project_create.md)|project|Creates a project object.|
|[PATCH project](../api/dynamics_project_update.md)|project|Updates a project object.|



## Properties

| Property           | Type   |Description     |
|:-------------------|:-------|:---------------|
|id|GUID|The unique ID of the project. Non-editable.|
|number|string|Specifies the number of the project.|
|displayName|string|Specifies the project's name. This name will appear on all sales documents for the project.|

## JSON representation

Here is a JSON representation of the project resource.


```json
{
    "id": "GUID",
    "number": "string",
    "displayName": "string"
}
```
<!-- IMPORTANT: END>DO_NOT_EDIT -->



## See Also
[GET project](../api/dynamics_project_Get.md)  
[DELETE project](../api/dynamics_project_Delete.md)  
[POST project](../api/dynamics_project_Create.md)  
[PATCH project](../api/dynamics_project_Update.md)
