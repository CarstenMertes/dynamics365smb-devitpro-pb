---
title: (v1.0) Delete salesQuotes
description: (v1.0) Deletes a sales quote object in Dynamics 365 Business Central.
 
author: SusanneWindfeldPedersen
ms.custom: evergreen
ms.topic: reference
ms.devlang: al
ms.date: 05/01/2024
ms.update-cycle: 1095-days
ms.author: solsen
ms.reviewer: solsen
---

# Delete salesQuotes (v1.0)
Delete a salesQuote from [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v1.0/endpoints-apis-for-dynamics.md).
```
DELETE businesscentralPrefix/companies({id})/salesQuotes({id})
```

## Request headers (v1.0)

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |
|If-Match      |Required. When this request header is included and the eTag provided does not match the current tag on the **salesQuotes**, the **salesQuotes** will not be updated. |

## Request body (v1.0)
Do not supply a request body for this method.

## Response (v1.0)
If successful, this method returns ```204 No Content``` response code. It does not return anything in the response body.

## Example (v1.0)

**Request**

Here is an example of the request.

```json
DELETE https://{businesscentralPrefix}/api/v1.0/companies({id})/salesQuotes({id})
```

**Response** 

Here is an example of the response. 

```json
HTTP/1.1 204 No Content
```

## Related information
[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)  

[Sales Quote](../resources/dynamics_salesquote.md)  
[Get Sales Quote](../api/dynamics_salesquote_get.md)  
[Create Sales Quote](../api/dynamics_create_salesquote.md)  
[Update Sales Quote](../api/dynamics_salesquote_update.md)  