---
title: CREATE projects  
description: Creates a project object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/01/2021
ms.author: solsen
---

# Create projects

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Create a project object in [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).
```
POST businesscentralPrefix/companies({id})/projects
```

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |
|Content-Type  |application/json|
|If-Match      |Required. When this request header is included and the eTag provided does not match the current tag on the **project**, the **project** will not be updated. |

## Request body
In the request body, supply a JSON representation of **project** object.

## Response
If successful, this method returns ```201 Created``` response code and a **project** object in the response body.

## Example

**Request**

Here is an example of a request.

```json
POST https://{businesscentralPrefix}/api/v2.0/companies({id})/projects
Content-type: application/json

{
    "number": "DEERFIELD, 8 WP",
    "displayName": "Setting up Eight Work Areas"
}
```

**Response**

Here is an example of the response. 

```json
HTTP/1.1 201 Created
Content-type: application/json

{
    "id": "22d7a1c5-bde4-ea11-bbf2-00155df3a615",
    "number": "DEERFIELD, 8 WP",
    "displayName": "Setting up Eight Work Areas"
}
```

## See also
[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)    
[project](../resources/dynamics_project.md)    
[Get project](dynamics_project_Get.md)    
[Delete project](dynamics_project_Delete.md)    
[Update project](dynamics_project_Update.md)    
