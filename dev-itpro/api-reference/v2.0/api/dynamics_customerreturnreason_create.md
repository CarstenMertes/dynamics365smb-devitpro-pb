---
title: Create customerReturnReasons
description: Creates a customer return reason object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 05/31/2024
ms.author: solsen
ms.reviewer: solsen
---

# Create customerReturnReasons

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Creates a customer return reason in [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request

Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).

```
POST businesscentralPrefix/companies({id})/customerReturnReasons
```

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |
|Content-Type  |application/json|

## Request body

In the request body, supply a JSON representation of a **customerReturnReason** object.

## Response

If successful, this method returns ```201 Created``` response code and a **customerReturnReason** object in the response body.

## Example

**Request**

Here's an example of the request.

```json
POST https://{businesscentralPrefix}/api/v2.0/companies({id})/customerReturnReasons
Content-type: application/json
{
  "code": "VARIANT",
  "description": "Incorrect item variant"
}
```

**Response**

Here's an example of the response.

```json
HTTP/1.1 201 Created
Content-type: application/json
{
    "id": "6ea22bf6-a449-ee11-ad0b-a1422c0f7f1f",
    "code": "VARIANT",
    "description": "Incorrect item variant"
}
```

## Related information

[Tips for working with the APIs](/dynamics365/business-central/dev-itpro/developer/devenv-connect-apps-tips)  
[customerReturnReason](../resources/dynamics_customerReturnReason.md)  
[GET customerReturnReason](dynamics_customerreturnreason_get.md)  
[DELETE customerReturnReason](dynamics_customerreturnreason_delete.md)  
[PATCH customerReturnReason](dynamics_customerreturnreason_update.md)  
