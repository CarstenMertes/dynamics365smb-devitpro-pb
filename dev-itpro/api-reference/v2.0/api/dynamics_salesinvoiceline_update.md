---
title: Update salesInvoiceLines  
description: Updates a sales invoice line object in Dynamics 365 Business Central.
 
author: SusanneWindfeldPedersen

ms.topic: reference
ms.devlang: al
ms.date: 04/01/2021
ms.author: solsen
---

# Update salesInvoiceLines

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Update the properties of a sales invoice line object for [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).

```
PATCH businesscentralPrefix/companies({id})/salesInvoices({id})/salesInvoiceLines({salesInvoiceLineId})
PATCH businesscentralPrefix/companies({id})/salesInvoiceLines({salesInvoiceLineId})
```

## Request headers

|Header|Value|
|------|-----|
|Authorization |Bearer {token}. Required.|
|Content-Type  |application/json|
|If-Match      |Required. When this request header is included and the eTag provided does not match the current tag on the **salesInvoiceLines**, the **salesInvoiceLines** will not be updated. |

## Request body
In the request body, supply the values for relevant fields that should be updated. Existing properties that are not included in the request body will maintain their previous values or be recalculated based on changes to other property values. For best performance you shouldn't include existing values that haven't changed.

## Response
If successful, this method returns a ```200 OK``` response code and an updated **salesInvoiceLines** object in the response body.

## Example

**Request**

Here is an example of the request.
```json
PATCH https://{businesscentralPrefix}/api/v2.0/companies({id})/salesInvoices{id}/salesInvoiceLines({salesInvoiceLineId})
Content-type: application/json

{
  "discountAmount": 0
}
```

**Response**

Here is an example of the response. 

> [!NOTE]  
>   The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```json
HTTP/1.1 200 OK
Content-type: application/json

{
    "id": "238cb9c0-44e3-ea11-bb43-000d3a2feca1",
    "documentId": "9e0f5c9c-44e3-ea11-bb43-000d3a2feca1",
    "sequence": 10000,
    "itemId": "02a6738a-44e3-ea11-bb43-000d3a2feca1",
    "accountId": "00000000-0000-0000-0000-000000000000",
    "lineType": "Item",
    "lineObjectNumber": "1928-S",
    "description": "AMSTERDAM Lamp",
    "unitOfMeasureId": "5ca6738a-44e3-ea11-bb43-000d3a2feca1",
    "unitOfMeasureCode": "PCS",
    "unitPrice": 54.9,
    "quantity": 3,
    "discountAmount": 0,
    "discountPercent": 0,
    "discountAppliedBeforeTax": false,
    "amountExcludingTax": 164.7,
    "taxCode": "FURNITURE",
    "taxPercent": 5,
    "totalTaxAmount": 8.24,
    "amountIncludingTax": 172.94,
    "invoiceDiscountAllocation": 0,
    "netAmount": 164.7,
    "netTaxAmount": 8.24,
    "netAmountIncludingTax": 172.94,
    "shipmentDate": "2020-08-21",
    "itemVariantId": "00000000-0000-0000-0000-000000000000",
    "locationId": "00000000-0000-0000-0000-000000000000"
}
```

## See also
[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)    
[salesinvoiceline](../resources/dynamics_salesinvoiceline.md)    
[Get salesinvoiceline](dynamics_salesinvoiceline_Get.md)    
[Delete salesinvoiceline](dynamics_salesinvoiceline_Delete.md)    
[Create salesinvoiceline](dynamics_salesinvoiceline_Create.md)    
