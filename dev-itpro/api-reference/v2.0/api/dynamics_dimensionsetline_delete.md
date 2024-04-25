---
title: DELETE dimensionSetLines  
description: Deletes dimensionSetLine  in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/01/2021
ms.author: solsen
---

# Delete dimensionSetLines

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Deletes dimensionSetLines in [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).
```
DELETE businesscentralPrefix/companies({id})/salesOrders({id})/dimensionSetLines({id})
DELETE businesscentralPrefix/companies({id})/journalLines({id})/dimensionSetLines({id})
DELETE businesscentralPrefix/companies({id})/salesOrderLines({id})/dimensionSetLines({id})
DELETE businesscentralPrefix/companies({id})/salesQuotes({id})/dimensionSetLines({id})
DELETE businesscentralPrefix/companies({id})/salesQuoteLines({id})/dimensionSetLines({id})
DELETE businesscentralPrefix/companies({id})/salesCreditMemos({id})/dimensionSetLines({id})
DELETE businesscentralPrefix/companies({id})/salesCreditMemoLines({id})/dimensionSetLines({id})
DELETE businesscentralPrefix/companies({id})/salesInvoices({id})/dimensionSetLines({id})
DELETE businesscentralPrefix/companies({id})/salesInvoiceLines({id})/dimensionSetLines({id})
DELETE businesscentralPrefix/companies({id})/purchaseInvoices({id})/dimensionSetLines({id})
DELETE businesscentralPrefix/companies({id})/purchaseInvoiceLines({id})/dimensionSetLines({id})
DELETE businesscentralPrefix/companies({id})/generalLedgerEntries({id})/dimensionSetLines({id})
DELETE businesscentralPrefix/companies({id})/timeRegistrationEntries({id})/dimensionSetLines({id})
DELETE businesscentralPrefix/companies({id})/purchaseOrders({id})/dimensionSetLines({id})
DELETE businesscentralPrefix/companies({id})/purchaseOrderLines({id})/dimensionSetLines({id})

```

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |
|If-Match       |Required. When this request header is included and the eTag provided does not match the current tag on the **dimensionSetLine**, the **dimensionSetLine** will not be updated. |

## Request body
Do not supply a request body for this method.

## Response
If successful, this method returns a ```204 No Content``` response code and it deletes the dimensionSetLine .

## Example

**Request**

Here is an example of the request.

```json
DELETE https://{businesscentralPrefix}/api/v2.0/companies({id})/salesOrders({id})/dimensionSetLines({id})
```

**Response** 

Here is an example of the response. 

```json
HTTP/1.1 204 No Content
```



## See also
[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)    
[dimensionsetline](../resources/dynamics_dimensionsetline.md)    
[Get dimensionsetline](dynamics_dimensionsetline_Get.md)    
[Create dimensionsetline](dynamics_dimensionsetline_Create.md)    
[Update dimensionsetline](dynamics_dimensionsetline_Update.md)    
