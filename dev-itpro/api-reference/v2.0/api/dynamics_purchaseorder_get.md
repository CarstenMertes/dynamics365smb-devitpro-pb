---
title: Get purchaseOrders  
description: Gets a purchase order object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/01/2021
ms.author: solsen
---

<!-- NOTE: This article is an auto-generated stub from the metadata file. -->
<!-- The sections marked with an EDIT_IS_REQUIRED require manual editing. -->
# Get purchaseOrders

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Retrieves the properties and relationships of a purchase order object for [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request

Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).

```
GET businesscentralPrefix/companies({id})/purchaseOrders({id})
```

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |

## Request body

Do not supply a request body for this method.

## Response

If successful, this method returns a ```200 OK``` response code and a **purchaseOrder** object in the response body.

## Example

**Request**

Here is an example of the request.

```json
GET https://{businesscentralPrefix}/api/v2.0/companies({id})/purchaseOrders({id})
```

**Response**
Here is an example of the response.


```json
{
   "id": "5d115c9c-44e3-ea11-bb43-000d3a2feca1",
   "number": "108001",
   "orderDate": "2021-01-01",
   "postingDate": "2021-01-01",
   "dueDate": "2021-01-01",
   "vendorId" : "",
   "vendorNumber": "20000",
   "vendorName": "First Up Consultants",
   "payToName": "First Up Consultants",
   "payToVendorId": "Evan McIntosh",
   "payToVendorNumber": "20000",
   "shipToName": "First Up Consultants",
   "shipToContact": "Evan McIntosh",
   "buyFromAddressLine1": "100 Day Drive",
   "buyFromAddressLine2": "",
   "buyFromCity": "Chicago",
   "buyFromCountry": "US",
   "buyFromState": "IL",
   "buyFromPostCode": "61236",
   "shipToAddressLine1": "100 Day Drive",
   "shipToAddressLine2": "",
   "shipToCity": "Chicago",
   "shipToCountry": "US",
   "shipToState": "IL",
   "shipToPostCode": "61236",
   "payToAddressLine1": "100 Day Drive",
   "payToAddressLine2": "",
   "payToCity": "Chicago",
   "payToCountry": "US",
   "payToState": "IL",
   "payToPostCode": "61236",
   "currencyId" : "00000000-0000-0000-0000-000000000000",
   "currencyCode": "USD",
   "pricesIncludeTax" : false,
   "paymentTermsId" : "04a5738a-44e3-ea11-bb43-000d3a2feca1",
   "shipmentMethodId" : "93f5638a-55e3-jk22-aa32-211d3a2fdce5",
   "purchaser" : "First Up Consultants",
   "requestedReceiptDate" : "2021-01-01",
   "discountAmount" : 0,
   "discountAppliedBeforeTax" : true,
   "totalAmountExcludingTax": 3122.8,
   "totalTaxAmount": 187.37,
   "totalAmountIncludingTax": 3310.17,
   "fullyReceived" : true,
   "status" : "In Review",
   "lastModifiedDateTime": "2021-01-01"
}
```

## See Also

[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)  
[purchaseOrder](../resources/dynamics_purchaseOrder.md)  
[DELETE purchaseOrder](dynamics_purchaseorder_delete.md)  
[POST purchaseOrder](dynamics_purchaseorder_create.md)  
[PATCH purchaseOrder](dynamics_purchaseorder_update.md)  
