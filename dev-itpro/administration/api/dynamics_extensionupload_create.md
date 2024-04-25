---
title: Create extensionUpload
description: Creates an extension upload object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/01/2021
ms.author: solsen
---

<!-- NOTE: This article is an auto-generated stub from the metadata file. -->
<!-- The sections marked with an EDIT_IS_REQUIRED require manual editing. -->
# Create extensionUpload

Creates an extension upload in [!INCLUDE[d365fin_long_md](../../includes/d365fin_long_md.md)].

## Bound Actions

| Actions         | Return Type  |Description|
|:---------------|:-------------|:----------|
|[Microsoft.NAV.upload](dynamics_extensionupload_create.md)|none|Uploads an extension.|

## HTTP requests

Replace the URL prefix for [!INCLUDE [prod_short](../../includes/prod_short.md)] depending on environment following the [guideline](../../api-reference/v2.0/enabling-apis-for-dynamics-nav.md).


### Insert extensionUpload
```
POST /microsoft/automation/v2.0/companies({companyId})/extensionUpload
```

### Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |
|Content-Type  |application/json|

### Request body

In the request body, supply a JSON representation of a [**extensionUpload** object](../resources/dynamics_extensionupload.md).

### Response

If successful, this method returns ```201 Created``` response code and a **extensionUpload** object in the response body.

### Upload extensionUpload
```json
POST /microsoft/automation/v2.0/companies({companyId})/extensionUpload({extensionUploadId})/Microsoft.NAV.upload
```

### Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |

### Request body

Do not supply a request body for this method.

### Response

If successful, this method returns ```204 No Content``` response code.


## Example

**Request**

Here is an example of the request.

```json
POST https://api.businesscentral.dynamics.com/v2.0/{environment name}/api/microsoft/automation/v2.0/companies({companyId})/extensionUpload
Content-type: application/json
{
    "schedule" : "Current version",
    "schemaSyncMode": "Add"
}
```

**Response**
Here is an example of the response.

```json
HTTP/1.1 201 Created
Content-type: application/json
{
    "systemId" : "f99be650-07ce-45df-a285-3afe69a953eb",
    "schedule" : "Current version",
    "schemaSyncMode": "Add",
    "extensionContent" : ""
}
```

## See Also

[Tips for working with the APIs](../../developer/devenv-connect-apps-tips.md)  
[extensionUpload](../resources/dynamics_extensionUpload.md)
