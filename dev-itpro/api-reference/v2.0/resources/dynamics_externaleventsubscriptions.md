---
title: externalEventSubscriptions resource type
description: Represents external event subscriptions used to subscribe to business events for integration with Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/08/2026
ms.author: solsen
ms.reviewer: solsen
---

# externalEventSubscriptions resource type

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Represents an external event subscription in [!INCLUDE[prod_short](../../../includes/prod_short.md)]. External event subscriptions allow you to subscribe to business events and receive notifications at a specified URL.

> [!NOTE]
> For information about enabling APIs for [!INCLUDE[prod_short](../../../includes/prod_short.md)] see [Enabling the APIs for Dynamics 365 Business Central](../enabling-apis-for-dynamics-nav.md).

## Methods

| Method | Return Type|Description |
|:--------------------|:-----------|:-------------------------|
|[GET externalEventSubscriptions](../api/dynamics_externaleventsubscriptions_get.md)|externalEventSubscriptions|Gets an external event subscription object.|
|[DELETE externalEventSubscriptions](../api/dynamics_externaleventsubscriptions_delete.md)|none|Deletes an external event subscription object.|
|[POST externalEventSubscriptions](../api/dynamics_externaleventsubscriptions_create.md)|externalEventSubscriptions|Creates an external event subscription object.|
|[PATCH externalEventSubscriptions](../api/dynamics_externaleventsubscriptions_update.md)|externalEventSubscriptions|Updates an external event subscription object.|

## Properties

| Property           | Type   |Description     |
|:-------------------|:-------|:---------------|
|id|GUID|The unique ID of the external event subscription. Non-editable.|
|companyId|GUID|The ID of the company associated with the subscription.|
|timestamp|int64|The timestamp of the subscription for concurrency control.|
|appId|GUID|The ID of the app that defines the business event.|
|eventName|string|The name of the business event to subscribe to.|
|companyName|string|The name of the company associated with the subscription.|
|userId|GUID|The ID of the user who created the subscription.|
|notificationUrl|string|The URL to which webhook notifications are sent.|
|lastModifiedDateTime|datetime|The last datetime the subscription was modified. Read-Only.|
|clientState|string|A client state value delivered with every notification. Use this as a secret to verify the message or for managing state.|
|subscriptionType|string|The type of the subscription.|
|eventVersion|string|The version of the business event.|
|subscriptionState|string|The state of the subscription.|
|systemCreatedAt|datetime|The datetime the subscription was created.|
|systemCreatedBy|GUID|The ID of the user who created the subscription.|
|systemModifiedAt|datetime|The last datetime the subscription was modified.|
|systemModifiedBy|GUID|The ID of the user who last modified the subscription.|

## JSON representation

Here's a JSON representation of the externalEventSubscriptions resource.

```json
{
    "id": "d3e3a1b2-44e3-ea11-bb43-000d3a2feca1",
    "companyId": "a1b2c3d4-44e3-ea11-bb43-000d3a2feca1",
    "timestamp": 12345678,
    "appId": "00000000-0000-0000-0000-000000000000",
    "eventName": "SalesOrderPosted",
    "companyName": "CRONUS International Ltd.",
    "userId": "b4c5d6e7-44e3-ea11-bb43-000d3a2feca1",
    "notificationUrl": "https://contoso.com/api/businessevents",
    "lastModifiedDateTime": "2026-04-08T10:00:00Z",
    "clientState": "mySecretClientState",
    "subscriptionType": "ExternalBusinessEvent",
    "eventVersion": "1.0",
    "subscriptionState": "Active",
    "systemCreatedAt": "2026-04-08T10:00:00Z",
    "systemCreatedBy": "b4c5d6e7-44e3-ea11-bb43-000d3a2feca1",
    "systemModifiedAt": "2026-04-08T10:00:00Z",
    "systemModifiedBy": "b4c5d6e7-44e3-ea11-bb43-000d3a2feca1"
}
```

## Related information

[GET externalEventSubscriptions](../api/dynamics_externaleventsubscriptions_get.md)  
[DELETE externalEventSubscriptions](../api/dynamics_externaleventsubscriptions_delete.md)  
[POST externalEventSubscriptions](../api/dynamics_externaleventsubscriptions_create.md)  
[PATCH externalEventSubscriptions](../api/dynamics_externaleventsubscriptions_update.md)
