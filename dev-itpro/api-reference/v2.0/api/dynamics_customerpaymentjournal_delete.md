---
title: DELETE customerPaymentJournals  
description: Deletes customerPaymentJournal  in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/01/2021
ms.author: solsen
---

# Delete customerPaymentJournals

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Delete a customer payment journal object from [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).
```
DELETE businesscentralPrefix/companies({id})/customerPaymentJournals({id})
```

## Request headers

|Header       |Value                     |
|-------------|--------------------------|
|Authorization|Bearer {token}. Required. |
|If-Match     |Required. When this request header is included and the eTag provided does not match the current tag on the **customerPaymentJournals**, the **customerPaymentJournals** will not be updated. |

## Request body

Do not supply a request body for this method.

## Response

If successful, this method returns ```204 No Content``` response code. It does not return anything in the response body.

## Example

**Request**

Here is an example of the request.

```json
DELETE https://{businesscentralPrefix}/api/v2.0/companies({id})/customerPaymentJournals({id})
```

**Response** 

Here is an example of the response. 

```json
HTTP/1.1 204 No Content
```

## See also
[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)    
[customerpaymentjournal](../resources/dynamics_customerpaymentjournal.md)    
[Get customerpaymentjournal](dynamics_customerpaymentjournal_Get.md)    
[Create customerpaymentjournal](dynamics_customerpaymentjournal_Create.md)    
[Update customerpaymentjournal](dynamics_customerpaymentjournal_Update.md)    
