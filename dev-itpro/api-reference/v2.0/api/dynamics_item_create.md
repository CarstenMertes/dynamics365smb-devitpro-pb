---
title: Create items  
description: Creates an item object in Dynamics 365 Business Central.
 
author: SusanneWindfeldPedersen

ms.topic: reference
ms.devlang: al
ms.date: 04/01/2021
ms.author: solsen
---

# Create items

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Create an item in [!INCLUDE[prod_short](../../../includes/prod_short.md)] for use on invoices, quotes, etc.

## HTTP request
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).
```
POST businesscentralPrefix/companies({id})/items
```

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |
|Content-Type  |application/json|
|If-Match      |Required. When this request header is included and the eTag provided does not match the current tag on the **item**, the **item** will not be updated. |

## Request body
In the request body, supply a JSON representation of an **items** object.

## Response
If successful, this method returns ```201 Created``` response code and an **items** object in the response body.

## Example
**Request**

Here is an example of a request.

```json
POST https://{businesscentralPrefix}/api/v2.0/companies({id})/items
Content-type: application/json

{
    "number": "1896-S",
    "displayName": "ATHENS Desk",
    "type": "Inventory",
    "itemCategoryId": "e21a6a90-44e3-ea11-bb43-000d3a2feca1",
    "itemCategoryCode": "TABLE",
    "blocked": false,
    "gtin": "",
    "unitPrice": 1000.8,
    "priceIncludesTax": false,
    "unitCost": 780.7,
    "taxGroupId": "9f196a90-44e3-ea11-bb43-000d3a2feca1",
    "taxGroupCode": "FURNITURE",
    "baseUnitOfMeasureId": "5ca6738a-44e3-ea11-bb43-000d3a2feca1",
    "baseUnitOfMeasureCode": "PCS"

}
```

**Response**

Here is an example of the response. 

> [!NOTE]  
>   The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```json
HTTP/1.1 201 Created
Content-type: application/json

{
    "id": "fca5738a-44e3-ea11-bb43-000d3a2feca1",
    "number": "1896-S",
    "displayName": "ATHENS Desk",
    "displayName2": "",
    "type": "Inventory",
    "itemCategoryId": "e21a6a90-44e3-ea11-bb43-000d3a2feca1",
    "itemCategoryCode": "TABLE",
    "blocked": false,
    "gtin": "",
    "inventory": 0,
    "unitPrice": 1000.8,
    "priceIncludesTax": false,
    "unitCost": 780.7,
    "taxGroupId": "9f196a90-44e3-ea11-bb43-000d3a2feca1",
    "taxGroupCode": "FURNITURE",
    "baseUnitOfMeasureId": "5ca6738a-44e3-ea11-bb43-000d3a2feca1",
    "baseUnitOfMeasureCode": "PCS",
    "generalProductPostingGroupId": "019b8ec1-d83d-ee11-be71-6045bde9cbf2",
    "generalProductPostingGroupCode": "RETAIL",
    "inventoryPostingGroupId": "039e8ec1-d83d-ee11-be71-6045bde9cbf2",
    "inventoryPostingGroupCode": "RESALE",
    "lastModifiedDateTime": "2020-08-21T00:24:19.347Z"
}
```

## See also
[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)    
[item](../resources/dynamics_item.md)    
[Get item](dynamics_item_Get.md)    
[Delete item](dynamics_item_Delete.md)    
[Update item](dynamics_item_Update.md)    
