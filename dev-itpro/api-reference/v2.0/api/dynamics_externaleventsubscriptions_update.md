---
title: Update externalEventSubscriptions
description: Update the properties of an external event subscription object in Dynamics 365 Business Central using the PATCH method.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/08/2026
ms.author: solsen
ms.reviewer: solsen
---

# Update externalEventSubscriptions

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Update the properties of an external event subscription object for [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request

Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).
```
PATCH businesscentralPrefix/companies({id})/externalEventSubscriptions({id})
```

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |
|Content-Type  |application/json|
|If-Match      |Required. When this request header is included and the eTag provided doesn't match the current tag on the **externalEventSubscriptions**, the **externalEventSubscriptions** won't be updated. |

## Request body

In the request body, supply the values for relevant fields that should be updated. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values. For best performance, don't include existing values that haven't changed.

## Response

If successful, this method returns a ```200 OK``` response code and an updated **externalEventSubscriptions** object in the response body.

## Example

**Request**

Here's an example of the request.

```json
PATCH https://{businesscentralPrefix}/api/v2.0/companies({id})/externalEventSubscriptions({id})
Content-type: application/json

{
    "notificationUrl": "https://contoso.com/api/businessevents/v2"
}
```

**Response**

Here's an example of the response.

> [!NOTE]
> The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```json
HTTP/1.1 200 OK
Content-type: application/json

{
    "id": "d3e3a1b2-44e3-ea11-bb43-000d3a2feca1",
    "companyId": "a1b2c3d4-44e3-ea11-bb43-000d3a2feca1",
    "appId": "00000000-0000-0000-0000-000000000000",
    "eventName": "SalesOrderPosted",
    "companyName": "CRONUS International Ltd.",
    "notificationUrl": "https://contoso.com/api/businessevents/v2",
    "lastModifiedDateTime": "2026-04-08T10:05:00Z",
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
[Create externalEventSubscriptions](dynamics_externaleventsubscriptions_create.md)
