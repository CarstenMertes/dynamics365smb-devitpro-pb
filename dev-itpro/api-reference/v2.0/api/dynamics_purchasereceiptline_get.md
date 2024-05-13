---
title: GET purchaseReceiptLines  
description: Gets a purchaseReceiptLine object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/01/2021
ms.author: solsen
---

# Get purchaseReceiptLines

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Retrieve the properties and relationships of a purchaseReceiptLine object for [!INCLUDE[prod_short](../../../includes/prod_short.md)]. 

## HTTP request

Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).

```
GET businesscentralPrefix/companies({id})/purchaseReceipts({id})/purchaseReceiptLines({purchaseReceiptLineId})
GET businesscentralPrefix/companies({id})/purchaseReceiptLines({purchaseReceiptLineId})
```

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |

## Request body
Do not supply a request body for this method.

## Response
If successful, this method returns a ```200 OK``` response code and an **purchaseReceiptLines** object in the response body.

## Example

**Request**

Here is an example of the request.

```json
GET https://{businesscentralPrefix}/api/v2.0/companies({id})/purchaseReceipts({id})/purchaseReceiptLines({purchaseReceiptLineId})
```

**Response**

Here is an example of the response. 

```json
{
   "id": "dd8db9c0-44e3-ea11-bb43-000d3a2feca1",
   "documentId": "5d115c9c-44e3-ea11-bb43-000d3a2feca1",
   "sequence": "10000",
   "lineType": "Item",
   "lineObjectNumber": "1896-S",
   "description": "ATHENS Desk",
   "unitOfMeasureCode": "PCS",
   "unitCost": 780.7,
   "quantity": 4,
   "discountPercent": 5,
   "taxPercent": 10,
   "expectedReceiptDate": "2021-01-01"
}
```


## See also

[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)  
[purchaseReceiptLine](../resources/dynamics_purchaseReceiptLine.md)  

