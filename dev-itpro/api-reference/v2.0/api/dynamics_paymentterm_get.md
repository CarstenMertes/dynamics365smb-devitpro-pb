---
title: GET paymentTerms  
description: Gets a paymentTerm object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/01/2021
ms.author: solsen
---

# Get paymentTerms

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Retrieve the properties and relationships of a payment terms object for [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).

```
GET businesscentralPrefix/companies({id})/paymentTerms({id})
```

## Request headers

|Header         |Value                     |
|---------------|--------------------------|
|Authorization  |Bearer {token}. Required. |

## Request body
Do not supply a request body for this method.

## Response
If successful, this method returns a ```200 OK``` response code and a **paymentTerms** object in the response body.

## Example

**Request**

Here is an example of the request.
```json
GET https://{businesscentralPrefix}/api/v2.0/companies({id})/paymentTerms({id})
```

**Response**

Here is an example of the response. 

> [!NOTE]  
>   The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```json
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
[Delete paymentterm](dynamics_paymentterm_Delete.md)    
[Create paymentterm](dynamics_paymentterm_Create.md)    
[Update paymentterm](dynamics_paymentterm_Update.md)    
