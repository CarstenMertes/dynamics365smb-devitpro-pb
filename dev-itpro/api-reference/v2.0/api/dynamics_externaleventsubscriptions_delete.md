---
title: Delete externalEventSubscriptions
description: Delete an external event subscription object from Dynamics 365 Business Central using the DELETE method.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/08/2026
ms.author: solsen
ms.reviewer: solsen
---

# Delete externalEventSubscriptions

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Delete an external event subscription from [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request

Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).
```
DELETE businesscentralPrefix/companies({id})/externalEventSubscriptions({id})
```

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |
|If-Match       |Required. When this request header is included and the eTag provided doesn't match the current tag on the **externalEventSubscriptions**, the **externalEventSubscriptions** won't be deleted. |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns ```204 No Content``` response code. It doesn't return anything in the response body.

## Example

**Request**

Here's an example of the request.

```json
DELETE https://{businesscentralPrefix}/api/v2.0/companies({id})/externalEventSubscriptions({id})
```

**Response**

Here's an example of the response.

```json
HTTP/1.1 204 No Content
```

## Related information

[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)  
[externalEventSubscriptions](../resources/dynamics_externaleventsubscriptions.md)  
[Get externalEventSubscriptions](dynamics_externaleventsubscriptions_get.md)  
[Create externalEventSubscriptions](dynamics_externaleventsubscriptions_create.md)  
[Update externalEventSubscriptions](dynamics_externaleventsubscriptions_update.md)
