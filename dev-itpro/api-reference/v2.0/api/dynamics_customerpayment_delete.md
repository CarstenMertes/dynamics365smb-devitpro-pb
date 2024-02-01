---
title: Delete customerPayments  
description: Deletes a customer payment object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/01/2021
ms.author: solsen
---

# Delete customerPayments

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Delete a customerPayment from [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).
```
DELETE businesscentralPrefix/companies({id})/customerPaymentsJournals({id})/customerPayments({id})
DELETE businesscentralPrefix/companies({id})/customerPayments({id})
```

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |
|If-Match       |Required. When this request header is included and the eTag provided does not match the current tag on the **customerPayment**, the **customerPayment** will not be updated. |

## Request body

Do not supply a request body for this method.

## Response

If successful, this method returns ```204 No Content``` response code. It does not return anything in the response body.

## Example

**Request**

Here is an example of the request.

```json
DELETE https://{businesscentralPrefix}/api/v2.0/companies({id})/customerPaymentsJournals({id})/customerPayments({id})
```

**Response** 

Here is an example of the response. 

```json
HTTP/1.1 204 No Content
```

## See also
[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)    
[customerpayment](../resources/dynamics_customerpayment.md)    
[Get customerpayment](dynamics_customerpayment_Get.md)    
[Create customerpayment](dynamics_customerpayment_Create.md)    
[Update customerpayment](dynamics_customerpayment_Update.md)    
