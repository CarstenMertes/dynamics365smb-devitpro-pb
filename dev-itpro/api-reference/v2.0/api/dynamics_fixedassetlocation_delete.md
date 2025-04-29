---
title: Delete fixedAssetLocations
description: Deletes a fixed asset location object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen

ms.topic: article
ms.devlang: al
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 05/31/2024
ms.author: solsen
ms.reviewer: solsen
---

<!-- NOTE: This article is an auto-generated stub from the metadata file. -->
<!-- The sections marked with an EDIT_IS_REQUIRED require manual editing. -->
# Delete fixedAssetLocations

Deletes a fixed asset location from [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request

Replaces the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).
<!-- START>EDIT_IS_REQUIRED. There URL for accessing the endpoint might be different or there might be more than one -->
```
DELETE businesscentralPrefix/companies({id})/fixedAssetLocations({id})
```
<!-- END>EDIT_IS_REQUIRED -->
## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |
|If-Match       |Required. When this request header is included and the eTag provided doesn't match the current tag on the **fixedAssetLocation**, the **fixedAssetLocation** won't be updated. |


## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns ```204 No Content``` response code and deletes the **fixedAssetLocation**. It doesn't return anything in the response body.

## Example

**Request**

Here's an example of the request.
<!-- START>EDIT_IS_REQUIRED. There URL for accessing the endpoint might be different -->
```json
DELETE https://{businesscentralPrefix}/api/v2.0/companies({id})/fixedAssetLocations({id})
```
<!-- END>EDIT_IS_REQUIRED -->
**Response**

Here's an example of the response.

```json
HTTP/1.1 204 No Content
```

## Related information

[Tips for working with the APIs](/dynamics365/business-central/dev-itpro/developer/devenv-connect-apps-tips)  
[fixedAssetLocation](../resources/dynamics_fixedAssetLocation.md)  
[GET fixedAssetLocation](dynamics_fixedassetlocation_get.md)  
[POST fixedAssetLocation](dynamics_fixedassetlocation_create.md)  
[PATCH fixedAssetLocation](dynamics_fixedassetlocation_update.md)  
