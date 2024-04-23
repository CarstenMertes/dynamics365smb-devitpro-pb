---
title: GET unitOfMeasures  
description: Gets a unitOfMeasure object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/01/2021
ms.author: solsen
---

# Get unitsOfMeasure

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Retrieve the properties and relationships of a units of measure object for [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../endpoints-apis-for-dynamics.md).

```
GET businesscentralPrefix/companies({id})/unitsOfMeasure({id})
```

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |

## Request body
Do not supply a request body for this method.

## Response
If successful, this method returns a ```200 OK``` response code and a **unitsOfMeasure** object in the response body.

## Example

**Request**

Here is an example of the request.
```json
GET https://{businesscentralPrefix}/api/v1.0/companies({id})/unitsOfMeasure({id})
```

**Response**

Here is an example of the response. 

> [!NOTE]  
>   The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```json
{
    "id": "53a6738a-44e3-ea11-bb43-000d3a2feca1",
    "code": "BOX",
    "displayName": "Box",
    "internationalStandardCode": "BX",
    "symbol": "",
    "lastModifiedDateTime": "2020-08-20T22:24:22.193Z"
}
```

## See also
[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)    
[unitofmeasure](../resources/dynamics_unitofmeasure.md)    
[Delete unitofmeasure](dynamics_unitofmeasure_Delete.md)    
[Create unitofmeasure](dynamics_unitofmeasure_Create.md)    
[Update unitofmeasure](dynamics_unitofmeasure_Update.md)    
