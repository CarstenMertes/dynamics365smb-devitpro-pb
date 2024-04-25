---
title: CREATE paymentMethods  
description: Creates a paymentMethod object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/01/2021
ms.author: solsen
---

# Create paymentMethods

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Create a payment method object in [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).
```
POST businesscentralPrefix/companies({id})/paymentMethods
```

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |
|Content-Type  |application/json|
|If-Match      |Required. When this request header is included and the eTag provided does not match the current tag on the **paymentMethod**, the **paymentMethod** will not be updated. |

## Request body
In the request body, supply a JSON representation of a **paymentMethods** object.

## Response
If successful, this method returns ```201 Created``` response code and a **paymentMethods** object in the response body.

## Example

**Request**

Here is an example of a request.

```json
POST https://{businesscentralPrefix}/api/v2.0/companies({id})/paymentMethods
Content-type: application/json

{
    "id": "3a196a90-44e3-ea11-bb43-000d3a2feca1",
    "code": "ACCOUNT",
    "displayName": "Payment on account"
}
```

**Response**

Here is an example of the response. 

> [!NOTE]  
>   The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```json
HTTP/1.1 201 Created
Content-type: application/json

{
    "id": "3a196a90-44e3-ea11-bb43-000d3a2feca1",
    "code": "ACCOUNT",
    "displayName": "Payment on account",
    "lastModifiedDateTime": "2020-08-21T00:48:51.487Z"
}
```

## See also
[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)    
[paymentmethod](../resources/dynamics_paymentmethod.md)    
[Get paymentmethod](dynamics_paymentmethod_Get.md)    
[Delete paymentmethod](dynamics_paymentmethod_Delete.md)    
[Update paymentmethod](dynamics_paymentmethod_Update.md)    
