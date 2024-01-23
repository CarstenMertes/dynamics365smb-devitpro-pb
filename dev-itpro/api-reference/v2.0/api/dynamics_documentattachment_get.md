---
title: Get documentAttachments
description: Gets a document attachment object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.service: "dynamics365-business-central"
ms.topic: reference
ms.devlang: al
ms.date: 03/08/2023
ms.author: solsen
---

<!-- NOTE: This article is an auto-generated stub from the metadata file. -->
<!-- The sections marked with an EDIT_IS_REQUIRED require manual editing. -->
# Get documentAttachments

Retrieves the properties and relationships of a document attachment object for [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request

Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).

```
GET businesscentralPrefix/companies({id})/documentAttachments({id})
```

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |

## Request body

Do not supply a request body for this method.

## Response

If successful, this method returns a ```200 OK``` response code and a **documentAttachment** object in the response body.

## Example

**Request**

Here is an example of the request.

```json
GET https://{businesscentralPrefix}/api/v2.0/companies({id})/documentAttachments({id})
```

**Response**

Here is an example of the response.


```json
{
    "id" : "",
    "fileName" : "",
    "byteSize" : "",
    "attachmentContent" : "",
    "parentType" : "",
    "parentId" : "",
    "lineNumber" : "",
    "documentFlowSales" : "",
    "documentFlowPurchase" : "",
    "lastModifiedDateTime" : ""
}
```

## See Also

[Tips for working with the APIs](/dynamics365/business-central/dev-itpro/developer/devenv-connect-apps-tips)  
[documentAttachment](../resources/dynamics_documentAttachment.md)  
[DELETE documentAttachment](dynamics_documentattachment_delete.md)  
[POST documentAttachment](dynamics_documentattachment_create.md)  
[PATCH documentAttachment](dynamics_documentattachment_update.md)  
