---
title: subscriptions resource type
description: A subscriptions object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.service: "dynamics365-business-central"
ms.topic: reference
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 04/28/2025
ms.author: solsen
---

# subscriptions resource type

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Represents a subscriptions in [!INCLUDE[prod_short](../../../includes/prod_short.md)].

> [!NOTE]
> For information about enabling APIs for [!INCLUDE[prod_short](../../../includes/prod_short.md)] see [Enabling the APIs for Dynamics 365 Business Central](../enabling-apis-for-dynamics-nav.md).

## Custom APIs

If you're subscribing to a custom API page, both the URL you send the subscription HTTP request to and the resource path you wish to subscribe to must include the `<APIPublisher>`, `<APIGroup>`, and `<APIVersion>` elements equivalent to: `api/<APIPublisher>/<APIGroup>/<APIVersion>/subscriptions`. For example, if your API publisher is `pub`, your API group is `grp`, and the version is 1.0, part of the URL will contain these elements `api/pub/grp/v1.0/subscriptions`.


## Methods

| Method | Return Type|Description |
|:--------------------|:-----------|:-------------------------|
|[GET subscriptions](../api/dynamics_subscriptions_get.md)|subscriptions|Gets a subscriptions object.|
|[DELETE subscriptions](../api/dynamics_subscriptions_delete.md)|none|Deletes a subscriptions object.|
|[POST subscriptions](../api/dynamics_subscriptions_create.md)|subscriptions|Creates a subscriptions object.|
|[PATCH subscriptions](../api/dynamics_subscriptions_update.md)|subscriptions|Updates a subscriptions object.|



## Properties

| Property           | Type   |Description     |
|:-------------------|:-------|:---------------|
|subscriptionId|string|Unique key for the subscription.|
|notificationUrl|string|URL to which webhook notifications are sent.|
|resource|string|URL for the resource being subscribed to. Supports relative and absolute URL.|
|timestamp|int64||
|userId|GUID|The ID of user that has created the subscriptions.|
|lastModifiedDateTime|datetime|The last datetime the subscriptions was modified. Read-Only.|
|clientState|string|Client state will be delivered with every notification. This can be used as a secret to verify message or for managing state if needed.|
|expirationDateTime|datetime|Date and time for when the webhook will expire.|
|systemCreatedAt|datetime|The datetime the company was created.|
|systemCreatedBy|GUID|The ID of the user who created the company.|
|systemModifiedAt|datetime|The last datetime the subscriptions was modified.|
|systemModifiedBy|GUID|The ID of the user who last modified the company.|

## JSON representation

Here is a JSON representation of the subscriptions resource.


```json
{
    "subscriptionId": "string",
    "notificationUrl": "string",
    "resource": "string",
    "timestamp": "int64",
    "userId": "GUID",
    "lastModifiedDateTime": "datetime",
    "clientState": "string",
    "expirationDateTime": "datetime",
    "systemCreatedAt": "datetime",
    "systemCreatedBy": "GUID",
    "systemModifiedAt": "datetime",
    "systemModifiedBy": "GUID"
}
```
<!-- IMPORTANT: END>DO_NOT_EDIT -->

## Related information

[GET subscriptions](../api/dynamics_subscriptions_Get.md)  
[DELETE subscriptions](../api/dynamics_subscriptions_Delete.md)  
[POST subscriptions](../api/dynamics_subscriptions_Create.md)  
[PATCH subscriptions](../api/dynamics_subscriptions_Update.md)
