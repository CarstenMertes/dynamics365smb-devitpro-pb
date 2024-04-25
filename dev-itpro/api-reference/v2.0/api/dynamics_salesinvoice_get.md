---
title: Get salesInvoices  
description: Gets a sales invoice object in Dynamics 365 Business Central. 
 
author: SusanneWindfeldPedersen

ms.topic: reference
ms.devlang: al
ms.date: 04/01/2021
ms.author: solsen
---

# Get salesInvoices

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Retrieve the properties and relationships of a sales object for [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).

```
GET businesscentralPrefix/companies({id})/salesInvoices({id})
```

## Request headers

|Header         |Value                     |
|---------------|--------------------------|
|Authorization  |Bearer {token}. Required. |

## Request body
Do not supply a request body for this method.

## Response
If successful, this method returns a ```200 OK``` response code and a **salesInvoices** object in the response body.

## Example

**Request**

Here is an example of the request.
```json
GET https://{businesscentralPrefix}/api/v2.0/companies({id})/salesInvoices({id})
```
To get more data for a salesInvoice, use expand:

``` .../salesInvoices({id})?$expand=salesInvoiceLines,customer```

**Response**

Here is an example of the response. 

> [!NOTE]  
>   The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```json
{
    "id": "9e0f5c9c-44e3-ea11-bb43-000d3a2feca1",
    "number": "PS-INV103001",
    "externalDocumentNumber": "",
    "invoiceDate": "2019-01-15",
    "postingDate": "2019-01-15",
    "dueDate": "2019-01-15",
    "customerPurchaseOrderReference": "",
    "customerId": "f3a5738a-44e3-ea11-bb43-000d3a2feca1",
    "customerNumber": "20000",
    "customerName": "Trey Research",
    "billToName": "Trey Research",
    "billToCustomerId": "f3a5738a-44e3-ea11-bb43-000d3a2feca1",
    "billToCustomerNumber": "20000",
    "shipToName": "Trey Research",
    "shipToContact": "Helen Ray",
    "sellToAddressLine1": "153 Thomas Drive",
    "sellToAddressLine2": "",
    "sellToCity": "Chicago",
    "sellToCountry": "US",
    "sellToState": "IL",
    "sellToPostCode": "61236",
    "billToAddressLine1": "153 Thomas Drive",
    "billToAddressLine2": "",
    "billToCity": "Chicago",
    "billToCountry": "US",
    "billToState": "IL",
    "billToPostCode": "61236",
    "shipToAddressLine1": "153 Thomas Drive",
    "shipToAddressLine2": "",
    "shipToCity": "Chicago",
    "shipToCountry": "US",
    "shipToState": "IL",
    "shipToPostCode": "61236",
    "currencyId": "00000000-0000-0000-0000-000000000000",
    "currencyCode": "USD",
    "orderId": "00000000-0000-0000-0000-000000000000",
    "orderNumber": "",
    "paymentTermsId": "0ba5738a-44e3-ea11-bb43-000d3a2feca1",
    "shipmentMethodId": "00000000-0000-0000-0000-000000000000",
    "salesperson": "PS",
    "pricesIncludeTax": false,
    "remainingAmount": 0,
    "discountAmount": 0,
    "discountAppliedBeforeTax": true,
    "totalAmountExcludingTax": 164.7,
    "totalTaxAmount": 8.24,
    "totalAmountIncludingTax": 172.94,
    "status": "Paid",
    "lastModifiedDateTime": "2020-08-21T00:25:58.337Z",
    "phoneNumber": "",
    "email": "helen.ray@contoso.com"
}
```

## See also
[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)    
[salesinvoice](../resources/dynamics_salesinvoice.md)    
[Delete salesinvoice](dynamics_salesinvoice_Delete.md)    
[Create salesinvoice](dynamics_salesinvoice_Create.md)    
[Update salesinvoice](dynamics_salesinvoice_Update.md)    
