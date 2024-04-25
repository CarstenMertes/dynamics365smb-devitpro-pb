---
title: (v1.0) Create journals
description: (v1.0) Creates a journal object in Dynamics 365 Business Central.
 
author: SusanneWindfeldPedersen

ms.topic: reference
ms.devlang: al
ms.date: 04/01/2019
ms.author: solsen
---

# Create journals (v1.0)
Creates a journal in [!INCLUDE[prod_short](../../../includes/prod_short.md)]. 

## HTTP request (v1.0)
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v1.0/endpoints-apis-for-dynamics.md).

```
POST businesscentralPrefix/companies({id})/journals({id})
```

## Request headers (v1.0)

|Header        |Value                     |
|--------------|--------------------------|
|Authorization |Bearer {token}. Required. |
|Content-Type  |application/json          |

## Request body (v1.0)
In the request body, supply a JSON representation of a **journals** object.
## Response (v1.0)
If successful, this method returns ```201 Created``` response code and a **journals** object in the response body.

## Example (v1.0)

**Request**

Here is an example of a request.

```json
POST https://{businesscentralPrefix}/api/v1.0/companies({id})/journals
Content-type: application/json
```json
{
  "code": "DEFAULT"
}
```

**Response**

```json
HTTP/1.1 201 Created
Content-type: application/json

{
  "id": "id-value",
  "code": "DEFAULT",
  "displayName": "Default Journal Batch",
  "lastModifiedDateTime": "2017-05-17T11:30:01.313Z"
}
```

## See also
[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)  
[Graph Reference](../api/dynamics_graph_reference.md)  
  
[Journal](../resources/dynamics_journal.md)  
[Get Journal](../api/dynamics_journal_get.md)  
[Update Journal](../api/dynamics_journal_update.md)  
[Delete Journal](../api/dynamics_journal_delete.md)  