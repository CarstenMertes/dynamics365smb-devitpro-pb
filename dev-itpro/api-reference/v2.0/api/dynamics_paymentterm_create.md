---
title: CREATE paymentTerms  
description: Creates a paymentTerm object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/01/2021
ms.author: solsen
---

# Create paymentTerms

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Create a payment terms object in [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).
```
POST businesscentralPrefix/companies({id})/paymentTerms
```

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |
|Content-Type  |application/json|
|If-Match      |Required. When this request header is included and the eTag provided does not match the current tag on the **paymentTerm**, the **paymentTerm** will not be updated. |

## Request body
In the request body, supply a JSON representation of a **paymentTerms** object.

## Response
If successful, this method returns ```201 Created``` response code and a **paymentTerms** object in the response body.

## Example

**Request**

Here is an example of a request.

```json
POST https://{businesscentralPrefix}/api/v2.0/companies({id})/paymentTerms
Content-type: application/json

{
    "code": "10 DAYS",
    "displayName": "Net 10 days",
    "dueDateCalculation": "10D",
    "discountDateCalculation": "",
    "discountPercent": 0,
    "calculateDiscountOnCreditMemos": false
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
    "id": "01a5738a-44e3-ea11-bb43-000d3a2feca1",
    "code": "10 DAYS",
    "displayName": "Net 10 days",
    "dueDateCalculation": "10D",
    "discountDateCalculation": "",
    "discountPercent": 0,
    "calculateDiscountOnCreditMemos": false,
    "lastModifiedDateTime": "2020-08-21T00:24:12.633Z"
}
```


## See also
[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)    
[paymentterm](../resources/dynamics_paymentterm.md)    
[Get paymentterm](dynamics_paymentterm_Get.md)    
[Delete paymentterm](dynamics_paymentterm_Delete.md)    
[Update paymentterm](dynamics_paymentterm_Update.md)    
