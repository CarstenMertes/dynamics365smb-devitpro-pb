---
title: Update taxAreas  
description: Updates a tax areas object in Dynamics 365 Business Central. 
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/01/2021
ms.author: solsen
---

# Update taxAreas

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Update the properties of a tax area object for [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).

```
PATCH businesscentralPrefix/companies({id})/taxAreas({id})
```

## Request headers

|Header|Value|
|------|-----|
|Authorization |Bearer {token}. Required.|
|Content-Type  |application/json|
|If-Match      |Required. When this request header is included and the eTag provided does not match the current tag on the **taxAreas**, the **taxAreas** will not be updated. |

## Request body
In the request body, supply the values for relevant fields that should be updated. Existing properties that are not included in the request body will maintain their previous values or be recalculated based on changes to other property values. For best performance you shouldn't include existing values that haven't changed.

## Response
If successful, this method returns a ```200 OK``` response code and an updated **taxAreas** object in the response body.

## Example

**Request**

Here is an example of the request.
```json
PATCH https://{businesscentralPrefix}/api/v2.0/companies({id})/taxAreas({id})
Content-type: application/json

{
  "code": "ATLANTA, GA",
  "displayName": "tax area",
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
    "id": "90196a90-44e3-ea11-bb43-000d3a2feca1",
    "code": "ATLANTA, GA",
    "displayName": "ATLANTA, GA",
    "taxType": "tax area",
    "lastModifiedDateTime": "2020-08-21T00:24:25.847Z"
}
```

## See also
[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)    
[taxarea](../resources/dynamics_taxarea.md)    
[Get taxarea](dynamics_taxarea_Get.md)    
[Delete taxarea](dynamics_taxarea_Delete.md)    
[Create taxarea](dynamics_taxarea_Create.md)    
