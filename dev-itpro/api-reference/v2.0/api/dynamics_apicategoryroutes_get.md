---
title: Get apiCategoryRoutes
description: Retrieve the properties of API category route objects that describe available API publishers, groups, and versions in Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/08/2026
ms.author: solsen
ms.reviewer: solsen
---

# Get apiCategoryRoutes

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Retrieve the properties of an API category route object for [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request

Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).
```
GET businesscentralPrefix/companies({id})/apiCategoryRoutes
```

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a ```200 OK``` response code and an **apiCategoryRoutes** object in the response body.

**Request**

Here's an example of the request.

```json
GET https://{businesscentralPrefix}/api/v2.0/companies({id})/apiCategoryRoutes
```

**Response**

Here's an example of the response.

> [!NOTE]
> The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```json
{
    "route": "microsoft/api/v2.0",
    "publisher": "microsoft",
    "group": "api",
    "version": "v2.0"
}
```

## Related information

[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)  
[apiCategoryRoutes](../resources/dynamics_apicategoryroutes.md)
