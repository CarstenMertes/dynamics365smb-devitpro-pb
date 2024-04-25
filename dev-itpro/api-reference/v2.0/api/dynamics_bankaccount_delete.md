---
title: DELETE bankAccounts  
description: Deletes bankAccount  in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/01/2021
ms.author: solsen
---

# Delete bankAccounts

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Deletes bankAccounts in [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).
```
DELETE businesscentralPrefix/companies({id})/bankAccounts({id})
```

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |
|If-Match       |Required. When this request header is included and the eTag provided does not match the current tag on the **bankAccount**, the **bankAccount** will not be updated. |


## Request body
Do not supply a request body for this method.

## Response
If successful, this method returns ```204 No Content``` response code and deletes the **bankAccount**. It does not return anything in the response body.

## Example

**Request**

Here is an example of the request.

```json
DELETE https://{businesscentralPrefix}/api/v2.0/companies({id})/bankAccounts({id})
```

**Response** 

Here is an example of the response. 

```json
HTTP/1.1 204 No Content
```



## See also
[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)    
[bankaccount](../resources/dynamics_bankaccount.md)    
[Get bankaccount](dynamics_bankaccount_Get.md)    
[Create bankaccount](dynamics_bankaccount_Create.md)    
[Update bankaccount](dynamics_bankaccount_Update.md)    
