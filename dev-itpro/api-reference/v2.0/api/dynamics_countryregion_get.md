---
title: GET countryRegions  
description: Gets a countryRegion object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/01/2021
ms.author: solsen
---

# Get countriesRegions

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Retrieve the properties and relationships of a countries regions object for [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).
```
GET businesscentralPrefix/companies({id})/countriesRegions({id})
```

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |

## Request body
Do not supply a request body for this method.

## Response
If successful, this method returns a ```200 OK``` response code and a **countriesRegions** object in the response body.

## Example

**Request**

Here is an example of the request.
```json
GET https://{businesscentralPrefix}/api/v2.0/companies({id})/countriesRegions({id})
```

**Response**

Here is an example of the response. 

> [!NOTE]  
>   The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```json
{
    "id": "44a5738a-44e3-ea11-bb43-000d3a2feca1",
    "code": "AE",
    "displayName": "United Arab Emirates",
    "addressFormat": "City+ZIP Code",
    "lastModifiedDateTime": "2020-08-21T00:24:13.54Z"
}
```

## See also
[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)    
[countryregion](../resources/dynamics_countryregion.md)    
[Delete countryregion](dynamics_countryregion_Delete.md)    
[Create countryregion](dynamics_countryregion_Create.md)    
[Update countryregion](dynamics_countryregion_Update.md)    
