---
title: Update salespersonPurchasers
description: Updates a  salesperson purchaser object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/28/2025
ms.author: solsen
---

# Update salespersonPurchasers

Updates the properties of a salesperson purchaser object for [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request

Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).

```
PATCH businesscentralPrefix/companies({id})/salespersonPurchasers({id})
```

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |
|Content-Type  |application/json|
|If-Match      |Required. When this request header is included and the eTag provided doesn't match the current tag on the **salespersonPurchaser**, the **salesperson purchaser** won't be updated. |

## Request body

In the request body, supply the values for relevant fields that should be updated. Existing properties that aren't included in the request body will maintain their previous values or be recalculated based on changes to other property values. For best performance you shouldn't include existing values that haven't changed.

## Response

If successful, this method returns a ```200 OK``` response code and an updated **salespersonPurchaser** object in the response body.

## Example

**Request**

Here's an example of the request.

```json
PATCH https://{businesscentralPrefix}/api/v2.0/companies({id})/salespersonPurchasers({id})
Content-type: application/json
{
    "id" : ,
    "code" :
}
```

**Response**

Here's an example of the response.


```json
HTTP/1.1 200 OK
Content-type: application/json
{
    "id" : ,
    "code" : ,
    "displayName" : ,
    "email" : ,
    "email2" : ,
    "phoneNo" : ,
    "jobTitle" : ,
    "commisionPercent" : ,
    "privacyBlocked" : ,
    "blocked" : ,
    "lastModifiedDateTime" :
}
```

## Related information

[Tips for working with the APIs](/dynamics365/business-central/dev-itpro/developer/devenv-connect-apps-tips)  
[salespersonPurchaser](../resources/dynamics_salespersonPurchaser.md)  
[GET salespersonPurchaser](dynamics_salespersonpurchaser_get.md)  
[DELETE salespersonPurchaser](dynamics_salespersonpurchaser_delete.md)  
[POST salespersonPurchaser](dynamics_salespersonpurchaser_create.md)  
[GET salespersonPurchaser](dynamics_salespersonpurchaser_get.md)  
