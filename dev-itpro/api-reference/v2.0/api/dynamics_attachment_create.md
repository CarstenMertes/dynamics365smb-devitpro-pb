---
title: Create attachment  
description: Creates an attachment object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 02/01/2023
ms.author: solsen
---

# Create attachments

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Creates a attachment in [!INCLUDE[prod_short](../../../includes/prod_short.md)]. An attachment in the [!INCLUDE[prod_short](../../../includes/prod_short.md)] API is defined as an Incoming Document (table 130).

## HTTP request
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../endpoints-apis-for-dynamics.md).

```
POST businesscentralPrefix/companies({id})/attachments
```

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |
|Content-Type  |application/json|
|If-Match      |Required. When this request header is included and the eTag provided does not match the current tag on the **attachment**, the **attachment** will not be updated. |


## Request body
In the request body, supply a JSON representation of a **attachment** object.

## Response
If successful, this method returns ```201 Created``` response code and a **attachment** object in the response body.

## Example

**Request**

Here is an example of a request.

```json
POST https://{businesscentralPrefix}/api/v2.0/companies({id})/attachments({id})

Content-type: application/json
```json
{
    "parentId" : "0a077d18-45e3-ea11-bb43-000d3a2feca1",
    "fileName": "myPDF.pdf",
    "parentType": "Journal"
}

ParentId is the Id of the entity, for which an attachment is being created.

**Response**

```json
HTTP/1.1 201 Created
Content-type: application/json

{
    "id": "b282a6f1-bfe3-ea11-aa60-000d3ad7cacb",
    "parentId": "0a077d18-45e3-ea11-bb43-000d3a2feca1",
    "fileName": "myPDF.pdf",
    "byteSize": 0,
    "lastModifiedDateTime": "2020-08-21T15:06:53Z",
    "parentType": "Journal"
}
```

## See also
[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)    
[attachment](../resources/dynamics_attachment.md)    
[Get attachment](dynamics_attachment_Get.md)    
[Delete attachment](dynamics_attachment_Delete.md)    
[Update attachment](dynamics_attachment_Update.md)    
