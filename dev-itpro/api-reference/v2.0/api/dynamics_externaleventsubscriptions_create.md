---
title: Create externalEventSubscriptions
description: Create an external event subscription object in Dynamics 365 Business Central to subscribe to business events.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/08/2026
ms.author: solsen
ms.reviewer: solsen
---

# Create externalEventSubscriptions

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Create an external event subscription in [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request

Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).
```
POST businesscentralPrefix/companies({id})/externalEventSubscriptions
```

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |
|Content-Type  |application/json|

## Request body

In the request body, supply a JSON representation of an **externalEventSubscriptions** object.

## Response

If successful, this method returns ```201 Created``` response code and an **externalEventSubscriptions** object in the response body.

## Example

**Request**

Here's an example of a request.

```json
POST https://{businesscentralPrefix}/api/v2.0/companies({id})/externalEventSubscriptions
Content-type: application/json

{
    "appId": "00000000-0000-0000-0000-000000000000",
    "eventName": "SalesOrderPosted",
    "eventVersion": "1.0",
    "notificationUrl": "https://contoso.com/api/businessevents",
    "clientState": "mySecretClientState",
    "subscriptionType": "ExternalBusinessEvent"
}
```

**Response**

Here's an example of the response.

> [!NOTE]
> The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```json
HTTP/1.1 201 Created
Content-type: application/json

{
    "id": "d3e3a1b2-44e3-ea11-bb43-000d3a2feca1",
    "companyId": "a1b2c3d4-44e3-ea11-bb43-000d3a2feca1",
    "appId": "00000000-0000-0000-0000-000000000000",
    "eventName": "SalesOrderPosted",
    "companyName": "CRONUS International Ltd.",
    "userId": "b4c5d6e7-44e3-ea11-bb43-000d3a2feca1",
    "notificationUrl": "https://contoso.com/api/businessevents",
    "lastModifiedDateTime": "2026-04-08T10:00:00Z",
    "clientState": "mySecretClientState",
    "subscriptionType": "ExternalBusinessEvent",
    "eventVersion": "1.0",
    "subscriptionState": "Active"
}
```

## Related information

[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)  
[externalEventSubscriptions](../resources/dynamics_externaleventsubscriptions.md)  
[Get externalEventSubscriptions](dynamics_externaleventsubscriptions_get.md)  
[Delete externalEventSubscriptions](dynamics_externaleventsubscriptions_delete.md)  
[Update externalEventSubscriptions](dynamics_externaleventsubscriptions_update.md)
