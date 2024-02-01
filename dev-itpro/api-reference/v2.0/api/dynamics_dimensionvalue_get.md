---
title: Get dimensionValues  
description: Gets a dimension value object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/01/2021
ms.author: solsen
---

# Get dimensionValues

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Retrieve the properties and relationships of a dimension value object for [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## Prerequisites

## HTTP request
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).

```
GET businesscentralPrefix/companies({id})/dimensions({id})/dimensionValues({id})
GET businesscentralPrefix/companies({id})/dimensionValues({id})
```

## Request headers

|Header       |Value                     |
|-------------|--------------------------|
|Authorization|Bearer {token}. Required. |

## Request body
Do not supply a request body for this method.

## Response
If successful, this method returns a ```200 OK``` response code and a **dimensionValues** object in the response body.

## Example

**Request**

Here is an example of the request.

```json
GET https://{businesscentralPrefix}/api/v2.0/companies({id})/dimensions({id})/dimensionValues({id})
```

**Response**

Here is an example of the response. 

> [!NOTE]  
>   The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```json
{
    "id": "50c99ea7-bde4-ea11-bbf2-00155df3a615",
    "code": "PRIVATE",
    "dimensionId": "4fc99ea7-bde4-ea11-bbf2-00155df3a615",
    "displayName": "Private",
    "lastModifiedDateTime": "2020-08-22T21:23:11.437Z"
}
```

## See also
[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)    
[dimensionvalue](../resources/dynamics_dimensionvalue.md)    
