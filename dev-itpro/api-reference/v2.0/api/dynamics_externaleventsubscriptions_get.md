---
title: Get externalEventSubscriptions
description: Retrieve the properties of external event subscription objects in Dynamics 365 Business Central using the GET method.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/08/2026
ms.author: solsen
ms.reviewer: solsen
---

# Get externalEventSubscriptions

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Retrieve the properties and relationships of an external event subscription object for [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request

Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).
```
GET businesscentralPrefix/companies({id})/externalEventSubscriptions({id})
```

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a ```200 OK``` response code and an **externalEventSubscriptions** object in the response body.

**Request**

Here's an example of the request.

```json
GET https://{businesscentralPrefix}/api/v2.0/companies({id})/externalEventSubscriptions({id})
```

**Response**

Here's an example of the response.

> [!NOTE]
> The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```json
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
[Delete externalEventSubscriptions](dynamics_externaleventsubscriptions_delete.md)  
[Create externalEventSubscriptions](dynamics_externaleventsubscriptions_create.md)  
[Update externalEventSubscriptions](dynamics_externaleventsubscriptions_update.md)
