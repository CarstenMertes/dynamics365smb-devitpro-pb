---
title: (v1.0) Get item picture
description: (v1.0) Gets an item picture in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen

ms.topic: reference
ms.devlang: al
ms.date: 04/01/2019
ms.author: solsen
---

# Get item picture (v1.0)
Gets the item picture of the item in [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v1.0/endpoints-apis-for-dynamics.md). 
The following example gets the default dimensions of the item entity in the response body.

```
GET businesscentralPrefix/companies({companyId})/items({itemId})/picture
```
## Request header

|Header|Value|
|------|-----|
|Authorization| Bearer {token}. Required.|

## Request body (v1.0)
Do not supply a request body for this method.

## Response (v1.0) 

If successful, this method returns a `200 OK` response code and the **picture** in the response body.

## Example (v1.0) 
**Request**

```json
GET https://{businesscentralPrefix}/api/v1.0/companies({companyId})/items({itemId})/picture
```

**Response**  
Here is an example of the response.

> [!NOTE]  
> The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.



```json
{
  "id": "d0e5d5da-795a-4924-b376-13665f794cdd",
  "width": 500,
  "height": 496,
  "contentType": "image\jpeg",
  "content@odata.mediaEditLink": "https:\\api.businesscentral.dynamics-tie.com\v1.0\api\beta\companies(55c438d0-2f5c-44a0-9965-20b4923d0bef)\items(d0e5d5da-795a-4924-b376-13665f794cdd)\picture(d0e5d5da-795a-4924-b376-13665f794cdd)\content",
  "content@odata.mediaReadLink": "https:\\api.businesscentral.dynamics-tie.com\v1.0\api\beta\companies(55c438d0-2f5c-44a0-9965-20b4923d0bef)\items(d0e5d5da-795a-4924-b376-13665f794cdd)\picture(d0e5d5da-795a-4924-b376-13665f794cdd)\content"
}
```

## See also
[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)  

[Items](../resources/dynamics_item.md)  
[Create item picture](dynamics_item_create_picture.md)  
[Update item picture](dynamics_item_update_picture.md)  
[Delete item picture](dynamics_item_delete_defaultdimensions.md)  

