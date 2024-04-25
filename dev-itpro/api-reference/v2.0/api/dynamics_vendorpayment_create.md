---
title: CREATE vendorPayments  
description: Creates a vendorPayment object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/01/2021
ms.author: solsen
---

# Create vendorPayments

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Create a vendorPayment object in [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).

```
POST businesscentralPrefix/companies({id})/vendorPayments
```

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |
|Content-Type  |application/json|
|If-Match      |Required. When this request header is included and the eTag provided does not match the current tag on the **vendorPayment**, the **vendorPayment** will not be updated. |


## Request body
In the request body, supply a JSON representation of **vendorPayments** object.

## Response
If successful, this method returns ```201 Created``` response code and a **vendorPayments** object in the response body.

## Example

**Request**

Here is an example of a request.

```json
POST https://{businesscentralPrefix}/api/v2.0/companies({id})/vendorPayments
Content-type: application/json

{
PLACE CODE HERE.
}
```

**Response**

Here is an example of the response. 

```json
HTTP/1.1 201 Created
Content-type: application/json

{
PLACE CODE HERE.
}
```


## See also
[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)     
[vendorPayment](../resources/dynamics_vendorPayment.md)  
[Get vendorPayment](dynamics_vendorPayment_Get.md)   
[Delete vendorPayment](dynamics_vendorPayment_Delete.md)   
[Update vendorPayment](dynamics_vendorPayment_Update.md)   


