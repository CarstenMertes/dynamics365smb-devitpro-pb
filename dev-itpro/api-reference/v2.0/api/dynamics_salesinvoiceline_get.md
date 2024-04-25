---
title: Get salesInvoiceLines  
description: Gets a sales invoice line object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/01/2021
ms.author: solsen
---

# Get salesInvoiceLines

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Retrieve the properties and relationships of a sales invoice line object for [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## Prerequisites

## HTTP request
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).

```
GET businesscentralPrefix/companies({id})/salesInvoices({id})/salesInvoiceLines({salesInvoiceLineId})
GET businesscentralPrefix/companies({id})/salesInvoiceLines({salesInvoiceLineId})
```



## Request headers

|Header         |Value                     |
|---------------|--------------------------|
|Authorization  |Bearer {token}. Required. |

## Request body
Do not supply a request body for this method.

## Response
If successful, this method returns a ```200 OK``` response code and a **salesInvoiceLines** object in the response body.

## Example

**Request**

Here is an example of the request.
```json
GET https://{businesscentralPrefix}/api/v2.0/companies({id})/salesInvoices({id})/salesInvoiceLines({salesInvoiceLineId})
```

**Response**

Here is an example of the response. 

> [!NOTE]  
>   The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```json
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
    "itemVariantId": "00000000-0000-0000-0000-000000000000"
}
```

## See also
[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)    
[salesinvoiceline](../resources/dynamics_salesinvoiceline.md)    
[Delete salesinvoiceline](dynamics_salesinvoiceline_Delete.md)    
[Create salesinvoiceline](dynamics_salesinvoiceline_Create.md)    
[Update salesinvoiceline](dynamics_salesinvoiceline_Update.md)    
