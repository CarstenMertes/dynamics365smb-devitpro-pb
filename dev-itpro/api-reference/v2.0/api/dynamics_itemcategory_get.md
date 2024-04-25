---
title: GET itemCategories  
description: Gets a itemCategory object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/01/2021
ms.author: solsen
---

# Get itemCategories

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Retrieve the properties and relationships of an item category object for [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).

```
GET businesscentralPrefix/companies({id})/itemCategories({id})
GET businesscentralPrefix/companies({id})/items(id)/itemCategory({id})
```

## Request headers

|Header       |Value                    |
|-------------|-------------------------|
|Authorization|Bearer {token}. Required.|

## Request body
Do not supply a request body for this method.

## Response
If successful, this method returns a ```200 OK``` response code and an **itemCategories** object in the response body.

## Example

**Request**

Here is an example of the request.
```json
GET https://{businesscentralPrefix}/api/v2.0/companies({id})/itemCategories({id})
```

**Response**

Here is an example of the response. 

> [!NOTE]  
>   The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```json
{
    "id": "dd1a6a90-44e3-ea11-bb43-000d3a2feca1",
    "code": "CHAIR",
    "displayName": "Office Chair",
    "lastModifiedDateTime": "2020-08-21T00:24:31.777Z"
}
```


## See also
[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)    
[itemcategory](../resources/dynamics_itemcategory.md)    
[Delete itemcategory](dynamics_itemcategory_Delete.md)    
[Create itemcategory](dynamics_itemcategory_Create.md)    
[Update itemcategory](dynamics_itemcategory_Update.md)    
