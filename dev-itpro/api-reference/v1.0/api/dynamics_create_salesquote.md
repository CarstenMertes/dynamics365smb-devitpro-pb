---
title: (v1.0) Create salesQuotes
description: (v1.0) Creates a sales quote object in Dynamics 365 Business Central.
 
author: SusanneWindfeldPedersen

ms.topic: reference
ms.devlang: al
ms.date: 04/01/2019
ms.author: solsen
---

# Create salesQuotes (v1.0)
Create a sales quote object in [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request (v1.0)
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v1.0/endpoints-apis-for-dynamics.md).

```
POST businesscentralPrefix/companies({id})/salesQuotes
```

## Request headers (v1.0)

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required.    |
|Content-Type  |application/json    |

## Request body (v1.0)
In the request body, supply a JSON representation of a **salesQuotes** object.
## Response (v1.0)
If successful, this method returns ```201 Created``` response code and a **salesQuotes** object in the response body.

## Example (v1.0)

**Request**

Here is an example of a request.

```json
POST https://{businesscentralPrefix}/api/v1.0/companies({id})/salesQuotes
Content-type: application/json

{
  "id": "id-value",
  "number": "1006",
  "documentDate": "2016-12-31",
  "customerNumber": "10000",
  "currencyCode": "GBP",
  "paymentTermsId": "3bb5b4b6-ea4c-43ca-ba1c-3b69e29a6668"
}
```
## See also
[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)  

[Sales Quote](../resources/dynamics_salesquote.md)  
[Get Sales Quote](../api/dynamics_salesquote_get.md)  
[Update Sales Quote](../api/dynamics_salesquote_update.md)  
[Delete Sales Quote](../api/dynamics_salesquote_delete.md)  