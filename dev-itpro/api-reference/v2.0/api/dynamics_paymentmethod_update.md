---
title: UPDATE paymentMethods   
description: Updates a paymentMethod object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/01/2021
ms.author: solsen
---

# Update paymentMethods 

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Update the properties of a paymentMethod object for [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).
```
PATCH businesscentralPrefix/companies({id})/paymentMethods({id})
```

## Request headers

|Header|Value|
|------|-----|
|Authorization |Bearer {token}. Required.|
|Content-Type  |application/json|
|If-Match      |Required. When this request header is included and the eTag provided does not match the current tag on the **paymentMethod**, the **paymentMethod** will not be updated. |

## Request body
In the request body, supply the values for relevant fields that should be updated. Existing properties that are not included in the request body will maintain their previous values or be recalculated based on changes to other property values. For best performance you shouldn't include existing values that haven't changed.

## Response
If successful, this method returns a ```200 OK``` response code and an updated **paymentMethods** object in the response body.

## Example

**Request**

Here is an example of the request.

```json
PATCH https://{businesscentralPrefix}/api/v2.0/companies({id})/paymentMethods({id})
Content-type: application/json

{
  "displayName": "Personal Check Payment"
}
```

**Response**

Here is an example of the response. 

> [!NOTE]  
>   The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```json
HTTP/1.1 200 OK
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
[Create paymentmethod](dynamics_paymentmethod_Create.md)    
