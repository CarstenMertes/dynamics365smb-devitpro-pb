---
title: (v1.0) Delete irs1099Codes
description: (v1.0) Deletes an IRS 1099 code object in Dynamics 365 Business Central.
 
author: SusanneWindfeldPedersen

ms.topic: reference
ms.devlang: al
ms.date: 04/01/2019
ms.author: solsen
---

# Delete irs1099Codes (v1.0)
Delete a irs1099Codes object from [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v1.0/endpoints-apis-for-dynamics.md).
```
DELETE businesscentralPrefix/companies({id})/irs1099Codes({id})
```

## Request headers (v1.0)

|Header       |Value                     |
|-------------|--------------------------|
|Authorization|Bearer {token}. Required. |
|If-Match     |Required. When this request header is included and the eTag provided does not match the current tag on the **irs1099Codes**, the **irs1099Codes** will not be updated. |

## Request body (v1.0)
Do not supply a request body for this method.

## Response (v1.0)
If successful, this method returns ```204 No Content``` response code. It does not return anything in the response body.

## Example (v1.0)

**Request**

Here is an example of the request.

```json
DELETE https://{businesscentralPrefix}/api/v1.0/companies({id})/irs1099Codes({id})
```

**Response** 

Here is an example of the response. 

```json
HTTP/1.1 204 No Content
```

## See also
[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)  



[Error Codes](../dynamics_error_codes.md)  
[IRS 1099](../resources/dynamics_irs1099.md)  
[Get IRS 1099](../api/dynamics_irs1099_get.md)  
[Post IRS 1099](../api/dynamics_create_irs1099.md)  
[Patch IRS 1099](../api/dynamics_irs1099_update.md)  