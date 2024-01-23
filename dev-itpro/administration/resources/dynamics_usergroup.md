---
title: userGroup resource type | Microsoft Docs
description: An user group object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 12/03/2023
ms.author: solsen
---

# userGroup resource type

<!-- START>DO_NOT_EDIT -->
<!-- IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT. -->
Represents an user group in [!INCLUDE[d365fin_long_md](../../includes/d365fin_long_md.md)].

> [!NOTE]
> For information about enabling APIs for [!INCLUDE [prod_short](../../includes/prod_short.md)] see [Enabling the APIs for Dynamics 365 Business Central](../../api-reference/v2.0/enabling-apis-for-dynamics-nav.md).

> [!NOTE]  
> User groups are replaced with [security groups](../../upgrade/deprecated-features-user-groups.md) and will be deprecated in version 25. For more information, see [security group APIs](../resources/dynamics_securitygroup.md) and [Control Access to Business Central Using Security Groups](/dynamics365/business-central/ui-security-groups).

## Methods

| Method | Return Type|Description |
|:--------------------|:-----------|:-------------------------|
|[GET userGroup](../api/dynamics_usergroup_get.md)|userGroup|Gets a user group object.|
|[DELETE userGroup](../api/dynamics_usergroup_delete.md)|none|Deletes a user group object.|
|[POST userGroup](../api/dynamics_usergroup_create.md)|userGroup|Creates a user group object.|
|[PATCH userGroup](../api/dynamics_usergroup_update.md)|userGroup|Updates a user group object.|


## Navigation

| Navigation |Return Type| Description |
|:----------|:----------|:-----------------|
|[userGroupPermissions](dynamics_usergrouppermission.md)|userGroupPermissions |Gets the permissions of the userGroup.|
|[profile](dynamics_profile.md)|profile |Gets the profile of the userGroup.|

## Properties

| Property           | Type   |Description     |
|:-------------------|:-------|:---------------|
|id|GUID|The unique ID of the user group. Non-editable.|
|code|string|The code of the user group.|
|displayName|string|Specifies the user group's name. This name will appear on all sales documents for the user group.|
|defaultProfileID|string|The ID of the defaultProfile.|
|assignToAllNewUsers|boolean|If true, all new users are assigned to user group.|

## JSON representation

Here is a JSON representation of the userGroup resource.


```json
{
    "id": "GUID",
    "code": "string",
    "displayName": "string",
    "defaultProfileID": "string",
    "assignToAllNewUsers": "boolean"
}
```
<!-- IMPORTANT: END>DO_NOT_EDIT -->

## See Also
[GET userGroup](../api/dynamics_usergroup_get.md)  
[DELETE userGroup](../api/dynamics_usergroup_delete.md)  
[POST userGroup](../api/dynamics_usergroup_create.md)   
[PATCH userGroup](../api/dynamics_usergroup_update.md)  
