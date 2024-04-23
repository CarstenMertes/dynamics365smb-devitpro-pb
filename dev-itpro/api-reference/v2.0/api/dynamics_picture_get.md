---
title: Get picture  
description: Gets a picture object in Dynamics 365 Business Central. 
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/01/2021
ms.author: solsen
---

# Get picture

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Retrieve the properties and relationships of a picture object for [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guidelines](../../v2.0/endpoints-apis-for-dynamics.md).
```
GET businesscentralPrefix/companies({companyId})/items({itemId})/picture
GET businesscentralPrefix/companies({companyId})/employees({employeeId})/picture
GET businesscentralPrefix/companies({companyId})/vendors({vendorId})/picture
GET businesscentralPrefix/companies({companyId})/customers({customerId})/picture
GET businesscentralPrefix/companies({companyId})/contacts({contactId})/picture
```

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |

## Request body

Do not supply a request body for this method.

## Response
If successful, this method returns a ```200 OK``` response code and a **picture** object in the response body.

## Example

**Request**

Here is an example of the request.

**GET Metadata**

```json
GET https://{businesscentralPrefix}/api/v2.0/companies(companyId)/items(itemId)/picture
```
**Response**

Here is an example of the response.

> [!NOTE]  
> The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```json
{
    "id": "53049aad-bde4-ea11-bbf2-00155df3a615",
    "parentType": "Item", 
    "width": 400,
    "height": 400,
    "contentType": "image/jpeg",
    "pictureContent@odata.mediaEditLink": "http://bcserver:7048/BC/api/v2.0/companies(52e03390-bde4-ea11-bbf2-00155df3a615)/customers(53049aad-bde4-ea11-bbf2-00155df3a615)/picture(3ba68d90-3a48-ed11-bbb0-000d3a398903)/content",
    "pictureContent@odata.mediaReadLink": "http://bcserver:7048/BC/api/v2.0/companies(52e03390-bde4-ea11-bbf2-00155df3a615)/customers(53049aad-bde4-ea11-bbf2-00155df3a615)/picture(3ba68d90-3a48-ed11-bbb0-000d3a398903)/content"
}
```

**GET Content**

```json
GET https://{businesscentralPrefix}/api/v2.0/companies(companyId)/items(itemId)/picture(3ba68d90-3a48-ed11-bbb0-000d3a398903)/content
```

**Response**

Body is the raw image data.


## See also
[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)  
[picture](../resources/dynamics_picture.md)  
[Delete picture](dynamics_picture_Delete.md)  
[Update picture](dynamics_picture_Update.md)  
