---
title: GET vendorPayments  
description: Gets a vendorPayment object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/01/2021
ms.author: solsen
---

# Get vendorPayments

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Retrieve the properties and relationships of a vendorPayment object for [!INCLUDE[prod_short](../../../includes/prod_short.md)]. 


## HTTP request
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).
```
GET businesscentralPrefix/companies({id})/vendorPayments({id})
```

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |

## Request body
Do not supply a request body for this method.

## Response
If successful, this method returns a ```200 OK``` response code and an **vendorPayments** object in the response body.

## Example

**Request**

Here is an example of the request.
```json
GET https://{businesscentralPrefix}/api/v2.0/companies({id})/vendorPayments({id})
```

**Response**

Here is an example of the response. 

```json
{

}
```


## See also
[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)  
[vendorPayment](../resources/dynamics_vendorPayment.md)  
[Delete vendorPayment](dynamics_vendorPayment_Delete.md)   
[Create vendorPayment](dynamics_vendorPayment_Create.md)   
[Update vendorPayment](dynamics_vendorPayment_Update.md)   

