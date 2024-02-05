---
title: Delete salesOrderLines  
description: Deletes a sales order line object in Dynamics 365 Business Central.
 
author: SusanneWindfeldPedersen

ms.topic: reference
ms.devlang: al
ms.date: 04/01/2021
ms.author: solsen
---

# Delete salesOrderLines

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Delete a sales order line object from [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).
```
DELETE businesscentralPrefix/companies({id})/salesOrders({id})/salesOrderLines({salesCreditMemoLineId})
DELETE businesscentralPrefix/companies({id})/salesOrderLines({salesOrderLineId})
```

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |
|If-Match       |Required. When this request header is included and the eTag provided does not match the current tag on the **salesOrderLines**, the **salesOrderLines** will not be updated. |

## Request body
Do not supply a request body for this method.

## Response
If successful, this method returns ```204 No Content``` response code. It does not return anything in the response body.

## Example

**Request**

Here is an example of the request.

```json
DELETE https://{businesscentralPrefix}/api/v2.0/companies({id})/salesOrders({id})/salesOrderLines({salesOrderLineId})
```

**Response** 

Here is an example of the response. 

```json
HTTP/1.1 204 No Content
```

## See also
[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)    
[salesorderline](../resources/dynamics_salesorderline.md)    
[Get salesorderline](dynamics_salesorderline_Get.md)    
[Create salesorderline](dynamics_salesorderline_Create.md)    
[Update salesorderline](dynamics_salesorderline_Update.md)    
