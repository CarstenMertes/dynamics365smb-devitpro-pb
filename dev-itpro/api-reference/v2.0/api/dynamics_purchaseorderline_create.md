---
title: Create purchaseOrderLine  
description: Creates a purchase order line object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/01/2021
ms.author: solsen
---

<!-- NOTE: This article is an auto-generated stub from the metadata file. -->
<!-- The sections marked with an EDIT_IS_REQUIRED require manual editing. -->
# Create purchaseOrderLine

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Creates a purchase order line in [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request

Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).

```
POST businesscentralPrefix/companies({id})/purchaseOrders({id})/purchaseOrderLines
POST businesscentralPrefix/companies({id})/purchaseOrderLines
```

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |
|Content-Type  |application/json|
|If-Match      |Required. When this request header is included and the eTag provided does not match the current tag on the **purchaseOrderLine**, the **purchaseOrderLine** will not be updated. |

## Request body

In the request body, supply a JSON representation of a **purchaseOrderLine** object.

## Response

If successful, this method returns ```201 Created``` response code and a **purchaseOrderLine** object in the response body.


## Example

**Request**

Here is an example of the request.

```json
POST https://{businesscentralPrefix}/api/v2.0/companies({id})/purchaseOrderLines
Content-type: application/json
{
    "id": "1e8cb9c0-44e3-ea11-bb43-000d3a2feca1",
    "documentId": "960f5c9c-44e3-ea11-bb43-000d3a2feca1",
    "sequence": 10000,
    "itemId": "0ea6738a-44e3-ea11-bb43-000d3a2feca1",
    "accountId": "93f5638a-55e3-jk22-aa32-211d3a2fdce5",
    "lineType": "Item",
    "lineObjectNumber": "1996-S",
    "description": "ATLANTA Whiteboard, base",
    "unitOfMeasureId": "5ca6738a-44e3-ea11-bb43-000d3a2feca1",
    "unitOfMeasureCode": "PCS",
    "quantity": 12,
    "directUnitCost": 1397.3,
    "discountAmount": 0,
    "discountPercent": 0,
    "taxCode": "FURNITURE",
    "expectedReceiptDate": "2020-04-02",
    "invoiceQuantity": 12,
    "receiveQuantity": 12,
    "itemVariantId": "00000000-0000-0000-0000-000000000000",
    "locationId": "00000000-0000-0000-0000-000000000000"
}
```

**Response**
Here is an example of the response.

```json
HTTP/1.1 201 Created
Content-type: application/json
{
    "id": "1e8cb9c0-44e3-ea11-bb43-000d3a2feca1",
    "documentId": "960f5c9c-44e3-ea11-bb43-000d3a2feca1",
    "sequence": 10000,
    "itemId": "0ea6738a-44e3-ea11-bb43-000d3a2feca1",
    "accountId": "93f5638a-55e3-jk22-aa32-211d3a2fdce5",
    "lineType": "Item",
    "lineObjectNumber": "1996-S",
    "description": "ATLANTA Whiteboard, base",
    "unitOfMeasureId": "5ca6738a-44e3-ea11-bb43-000d3a2feca1",
    "unitOfMeasureCode": "PCS",
    "quantity": 12,
    "directUnitCost": 1397.3,
    "discountAmount": 0,
    "discountPercent": 0,
    "discountAppliedBeforeTax": false,
    "amountExcludingTax": 16767.6,
    "taxCode": "FURNITURE",
    "taxPercent": 6.00002,
    "totalTaxAmount": 1006.06,
    "amountIncludingTax": 17773.66,
    "invoiceDiscountAllocation": 0,
    "netAmount": 16767.6,
    "netTaxAmount": 1006.06,
    "netAmountIncludingTax": 17773.66,
    "expectedReceiptDate": "2020-04-02",
    "receivedQuantity": 0,
    "invoicedQuantity": 0,
    "invoiceQuantity": 12,
    "receiveQuantity": 12,
    "itemVariantId": "00000000-0000-0000-0000-000000000000",
    "locationId": "00000000-0000-0000-0000-000000000000"
}
```

## See Also

[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)  
[purchaseOrderLine](../resources/dynamics_purchaseOrderLine.md)  
[GET purchaseOrderLine](dynamics_purchaseorderline_get.md)  
[DELETE purchaseOrderLine](dynamics_purchaseorderline_delete.md)  
[PATCH purchaseOrderLine](dynamics_purchaseorderline_update.md)  
