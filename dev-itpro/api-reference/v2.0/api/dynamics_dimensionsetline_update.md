---
title: UPDATE dimensionSetLines   
description: Updates a dimensionSetLine object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/01/2021
ms.author: solsen
---

# Update dimensionSetLines 

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Update the properties of a dimensionSetLine object for [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).
```
PATCH businesscentralPrefix/companies({id})/salesOrders({id})/dimensionSetLines({id})
PATCH businesscentralPrefix/companies({id})/journalLines({id})/dimensionSetLines({id})
PATCH businesscentralPrefix/companies({id})/salesOrderLines({id})/dimensionSetLines({id})
PATCH businesscentralPrefix/companies({id})/salesQuotes({id})/dimensionSetLines({id})
PATCH businesscentralPrefix/companies({id})/salesQuoteLines({id})/dimensionSetLines({id})
PATCH businesscentralPrefix/companies({id})/salesCreditMemos({id})/dimensionSetLines({id})
PATCH businesscentralPrefix/companies({id})/salesCreditMemoLines({id})/dimensionSetLines({id})
PATCH businesscentralPrefix/companies({id})/salesInvoices({id})/dimensionSetLines({id})
PATCH businesscentralPrefix/companies({id})/salesInvoiceLines({id})/dimensionSetLines({id})
PATCH businesscentralPrefix/companies({id})/purchaseInvoices({id})/dimensionSetLines({id})
PATCH businesscentralPrefix/companies({id})/purchaseInvoiceLines({id})/dimensionSetLines({id})
PATCH businesscentralPrefix/companies({id})/generalLedgerEntries({id})/dimensionSetLines({id})
PATCH businesscentralPrefix/companies({id})/timeRegistrationEntries({id})/dimensionSetLines({id})
PATCH businesscentralPrefix/companies({id})/purchaseOrders({id})/dimensionSetLines({id})
PATCH businesscentralPrefix/companies({id})/purchaseOrderLines({id})/dimensionSetLines({id})

```

## Request headers

|Header|Value|
|------|-----|
|Authorization |Bearer {token}. Required.|
|Content-Type  |application/json|
|If-Match      |Required. When this request header is included and the eTag provided does not match the current tag on the **dimensionSetLine**, the **dimensionSetLine** will not be updated. |

## Request body
In the request body, supply the values for relevant fields that should be updated. Existing properties that are not included in the request body will maintain their previous values or be recalculated based on changes to other property values. For best performance you shouldn't include existing values that haven't changed.

## Response
If successful, this method returns a ```200 OK``` response code and an updated **dimensionSetLines ** object in the response body.

## Example

**Request**

Here is an example of the request.

```json
PATCH https://{businesscentralPrefix}/api/v2.0/companies({id})/salesOrders({id})/dimensionSetLines({id})
Content-type: application/json

{
    "code": "SALESGROUP",
    "displayName": "Sales Group",
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
    "id": "55c99ea7-bde4-ea11-bbf2-00155df3a615",
    "code": "SALESGROUP",
    "parentId": "85d8a1c5-bde4-ea11-bbf2-00155df3a615",
    "parentType": "Sales Order",
    "displayName": "Sales Group",
    "valueId": "56c99ea7-bde4-ea11-bbf2-00155df3a615",
    "valueCode": "HOME",
    "valueDisplayName": "Home"
}
```


## See also
[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)    
[dimensionsetline](../resources/dynamics_dimensionsetline.md)    
[Get dimensionsetline](dynamics_dimensionsetline_Get.md)    
[Delete dimensionsetline](dynamics_dimensionsetline_Delete.md)    
[Create dimensionsetline](dynamics_dimensionsetline_Create.md)    
