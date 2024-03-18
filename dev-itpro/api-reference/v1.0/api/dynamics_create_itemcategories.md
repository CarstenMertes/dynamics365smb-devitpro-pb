---
title: (v1.0) Create itemCategories
description: (v1.0) Creates an item category object in Dynamics 365 Business Central.
 
author: SusanneWindfeldPedersen

ms.topic: reference
ms.devlang: al
ms.date: 04/01/2019
ms.author: solsen
---

# Create itemCategories (v1.0)
Create an item category object [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request (v1.0)
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v1.0/endpoints-apis-for-dynamics.md).
```
POST businesscentralPrefix/companies({id})/itemCategories
```

## Request headers (v1.0)

|Header       |Value                    |
|-------------|-------------------------|
|Authorization|Bearer {token}. Required.|
|Content-Type |application/json         |

## Request body (v1.0)
In the request body, supply a JSON representation of an **itemCategories** object.
## Response (v1.0)
If successful, this method returns ```201 Created``` response code and an **itemCategories** object in the response body.

## Example (v1.0)

**Request**

Here is an example of a request.

```json
POST https://{businesscentralPrefix}/api/v1.0/companies({id})/itemCategories
Content-type: application/json

{
  "code": "CHAIR",
  "displayName": "Office Chair"
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
  "id": "id-value",
  "code": "CHAIR",
  "displayName": "Office Chair",
  "lastModifiedDateTime": "2017-03-15T02:21:24.047Z"
}
```



## See also
[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)  
  
[Item Categories](../resources/dynamics_itemcategories.md)  
[Get Item Categories](../api/dynamics_itemcategories_get.md)  
[Update Item Categories](../api/dynamics_itemcategories_update.md)  
[Delete Item Categories](../api/dynamics_itemcategories_delete.md)  