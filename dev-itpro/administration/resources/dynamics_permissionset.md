---
title: permissionSet resource type | Microsoft Docs
description: A permission set object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/01/2021
ms.author: solsen
---

# permissionSet resource type

<!-- START>DO_NOT_EDIT -->
<!-- IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT. -->
Represents a permission set in [!INCLUDE[d365fin_long_md](../../includes/d365fin_long_md.md)].

> [!NOTE]
> For information about enabling APIs for [!INCLUDE [prod_short](../../includes/prod_short.md)] see [Enabling the APIs for Dynamics 365 Business Central](../../api-reference/v2.0/enabling-apis-for-dynamics-nav.md).


## Methods

| Method | Return Type|Description |
|:--------------------|:-----------|:-------------------------|
|[GET permissionSet](../api/dynamics_permissionset_get.md)|permissionSet|Gets a permission set object.|



## Properties

| Property           | Type   |Description     |
|:-------------------|:-------|:---------------|
|scope|string|Scope of the permission set.|
|appId|GUID|The ID of the App.|
|id|string|The unique ID of the permission set. Read-Only.|
|displayName|string|Specifies the permission set's name. This name will appear on all sales documents for the permission set.|
|extensionName|string|The name of the extension.|

## JSON representation

Here is a JSON representation of the permissionSet resource.


```json
{
    "scope": "string",
    "appId": "GUID",
    "id": "string",
    "displayName": "string",
    "extensionName": "string"
}
```
<!-- IMPORTANT: END>DO_NOT_EDIT -->

## See Also
[GET permissionSet](../api/dynamics_permissionset_get.md)  
