---
title: (v1.0) Update paymentMethods
description: (v1.0) Updates a payment method object in Dynamics 365 Business Central.
 
author: SusanneWindfeldPedersen

ms.topic: reference
ms.devlang: al
ms.date: 04/01/2019
ms.author: solsen
---

# Update paymentMethods (v1.0)
Update the properties of a payment method object for [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v1.0/endpoints-apis-for-dynamics.md).
```
PATCH businesscentralPrefix/companies({id})/paymentMethods({id})
```

## Request headers (v1.0)

|Header        |Value                     |
|--------------|--------------------------|
|Authorization |Bearer {token}. Required. |
|Content-Type  |application/json          |
|If-Match      |Required. When this request header is included and the eTag provided does not match the current tag on the **paymentMethods**, the **paymentMethods** will not be updated. |

## Request body (v1.0)
In the request body, supply the values for relevant fields that should be updated. Existing properties that are not included in the request body will maintain their previous values or be recalculated based on changes to other property values. For best performance you shouldn't include existing values that haven't changed.

## Response (v1.0)
If successful, this method returns a ```200 OK``` response code and an updated **paymentMethods** object in the response body.

## Example (v1.0)

**Request**

Here is an example of the request.
```json
PATCH https://{businesscentralPrefix}/api/v1.0/companies({id})/paymentMethods({id})
Content-type: application/json

{
  "displayName": "Personal Check Payment",
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
  "id": "id-value",
  "code": "CHECK",
  "displayName": "Personal Check Payment",
  "lastModifiedDateTime": "2017-03-22T08:35:48.33Z"
}
```


## See also
[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)  

[Payment Methods](../resources/dynamics_paymentmethods.md)  
[Get Payment Methods](../api/dynamics_paymentmethods_get.md)  
[Create Payment Methods](../api/dynamics_create_paymentmethods.md)  
[Delete Payment Methods](../api/dynamics_paymentmethods_delete.md)  