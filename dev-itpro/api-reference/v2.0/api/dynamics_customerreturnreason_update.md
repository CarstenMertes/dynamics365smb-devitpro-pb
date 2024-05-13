---
title: Update customerReturnReasons
description: Updates a  customer return reason object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 05/27/2021
ms.author: solsen
---

<!-- NOTE: This article is an auto-generated stub from the metadata file. -->
<!-- The sections marked with an EDIT_IS_REQUIRED require manual editing. -->
# Update customerReturnReasons

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Updates the properties of a customer return reason object for [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request

Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).

```
PATCH businesscentralPrefix/companies({id})/customerReturnReasons({id})
```

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |
|Content-Type  |application/json|
|If-Match      |Required. When this request header is included and the eTag provided does not match the current tag on the **customerReturnReason**, the **customer return reason** will not be updated. |

## Request body

In the request body, supply the values for relevant fields that should be updated. Existing properties that are not included in the request body will maintain their previous values or be recalculated based on changes to other property values. For best performance you shouldn't include existing values that haven't changed.

## Response

If successful, this method returns a ```200 OK``` response code and an updated **customerReturnReason** object in the response body.

## Example

**Request**

Here is an example of the request.

```json
PATCH https://{businesscentralPrefix}/api/v2.0/companies({id})/customerReturnReasons({id})
Content-type: application/json
{
  "description": "Wrong item variant"
}
```

**Response**

Here is an example of the response.

```json
HTTP/1.1 200 OK
Content-type: application/json
{
    "id": "6ea22bf6-a449-ee11-ad0b-a1422c0f7f1f",
    "code": "VARIANT",
    "description": "Wrong item variant"
}
```

## See Also

[Tips for working with the APIs](/dynamics365/business-central/dev-itpro/developer/devenv-connect-apps-tips)  
[customerReturnReason](../resources/dynamics_customerReturnReason.md)  
[GET customerReturnReason](dynamics_customerreturnreason_get.md)  
[DELETE customerReturnReason](dynamics_customerreturnreason_delete.md)  
[POST customerReturnReason](dynamics_customerreturnreason_create.md)  
