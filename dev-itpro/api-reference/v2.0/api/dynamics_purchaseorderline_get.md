---
title: Get purchaseOrderLines  
description: Gets a purchase order line object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/01/2021
ms.author: solsen
---

<!-- NOTE: This article is an auto-generated stub from the metadata file. -->
<!-- The sections marked with an EDIT_IS_REQUIRED require manual editing. -->
# Get purchaseOrderLines

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Retrieves the properties and relationships of a purchase order line object for [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request

Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).

```
GET businesscentralPrefix/companies({id})/purchaseOrders({id})/purchaseOrderLines({purchaseOrderLineId})
GET businesscentralPrefix/companies({id})/purchaseOrderLines({purchaseOrderLineId})
```

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |

## Request body

Do not supply a request body for this method.

## Response

If successful, this method returns a ```200 OK``` response code and a **purchaseOrderLine** object in the response body.

## Example

**Request**

Here is an example of the request.

```json
GET https://{businesscentralPrefix}/api/v2.0/companies({id})/purchaseOrderLines({purchaseOrderLineId})
```

**Response**
Here is an example of the response.

```json
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
    "itemVariantId": "00000000-0000-0000-0000-000000000000"
}
```

## See Also

[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)  
[purchaseOrderLine](../resources/dynamics_purchaseOrderLine.md)  
[DELETE purchaseOrderLine](dynamics_purchaseorderline_delete.md)  
[POST purchaseOrderLine](dynamics_purchaseorderline_create.md)  
[PATCH purchaseOrderLine](dynamics_purchaseorderline_update.md)  
