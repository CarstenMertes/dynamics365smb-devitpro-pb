---
title: (v1.0) Get salesCreditMemoLines
description: (v1.0) Gets a sales credit memo line in Dynamics 365 Business Central. 
 
author: SusanneWindfeldPedersen

ms.topic: reference
ms.devlang: al
ms.date: 04/01/2019
ms.author: solsen
---

# Get salesCreditMemoLines (v1.0)
Retrieve the properties and relationships of a sales credit memo line object for [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## Prerequisites

## HTTP request
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v1.0/endpoints-apis-for-dynamics.md).

```
GET businesscentralPrefix/companies({id})/salesCreditMemos({id})/salesCreditMemoLines({salesCreditMemoLineId})
```

## Request headers (v1.0)

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |

## Request body (v1.0)
Do not supply a request body for this method.

## Response (v1.0)
If successful, this method returns a ```200 OK``` response code and a **salesCreditMemoLines** object in the response body.

## Example (v1.0)

**Request**

Here is an example of the request.
```json
GET https://{businesscentralPrefix}/api/v1.0/companies({id})/salesCreditMemos({id})/salesCreditMemoLines({salesCreditMemoLineId})
```

**Response**

Here is an example of the response. 

> [!NOTE]  
>   The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```json
{
  "documentId": "id-value",
  "sequence": 10000,
  "itemId": "id-value",
  "accountId": "id-value",
  "lineType": "Item",
  "lineDetails": {
    "number": "GL000009",
    "displayName": "GL000009",
    "description": null
  },
  "description": "someText",
  "unitOfMeasureId": "id-value",
  "unitOfMeasure": {
    "code": "BOX",
    "displayName": "Box",
    "symbol": null,
    "unitConversion": null
  },
  "unitPrice": 71.1,
  "quantity": 96,
  "discountAmount": 0,
  "discountPercent": 0,
  "discountAppliedBeforeTax": false,
  "amountExcludingTax": 6825.6,
  "taxCode": "VAT10",
  "taxPercent": 10,
  "totalTaxAmount": 682.56,
  "amountIncludingTax": 7508.16,
  "invoiceDiscountAllocation": 0,
  "netAmount": 6825.6,
  "netTaxAmount": 682.56,
  "netAmountIncludingTax": 7508.16,
  "shipmentDate": "2015-02-24"
}
```

## See also
[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)  

[Sales Credit Memo Line](../resources/dynamics_salescreditmemoline.md)  
[Create Sales Credit Memo Line](../api/dynamics_create_salescreditmemoline.md)  
[Update Sales Credit Memo Line](../api/dynamics_salescreditmemoline_update.md)  
[Delete Sales Credit Memo Line](../api/dynamics_salescreditmemoline_delete.md)  