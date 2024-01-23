---
title: Update subscriptions
description: Updates a  subscriptions object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.service: "dynamics365-business-central"
ms.topic: reference
ms.devlang: al
ms.date: 08/25/2022
ms.author: solsen
---

<!-- NOTE: This article is an auto-generated stub from the metadata file. -->
<!-- The sections marked with an EDIT_IS_REQUIRED require manual editing. -->
# Update subscriptions

Updates the properties of a subscriptions object for [!INCLUDE [prod_short](../../includes/prod_short.md)].

## HTTP request

Replace the URL prefix for [!INCLUDE [prod_short](../../includes/prod_short.md)] depending on environment following the [guideline](../../api-reference/v2.0/endpoints-apis-for-dynamics.md).

```
PATCH businesscentralPrefix/companies({id})/subscriptions({id})
```

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |
|Content-Type  |application/json|
|If-Match      |Required. When this request header is included and the eTag provided does not match the current tag on the **subscriptions**, the **subscriptions** will not be updated. |

## Request body

In the request body, supply the values for relevant fields that should be updated. Existing properties that are not included in the request body will maintain their previous values or be recalculated based on changes to other property values. For best performance you shouldn't include existing values that haven't changed.

## Response

If successful, this method returns a ```200 OK``` response code and an updated **subscriptions** object in the response body.

## Example

**Request**

Here is an example of the request.

```json
PATCH https://{businesscentralPrefix}/api/v2.0/companies({id})/subscriptions({id})
Content-type: application/json
{
    "subscriptionId" : ,
    "notificationUrl" :
}
```

**Response**

Here is an example of the response.

```json
HTTP/1.1 200 OK
Content-type: application/json
{
    "subscriptionId" : ,
    "notificationUrl" : ,
    "resource" : ,
    "timestamp" : ,
    "userId" : ,
    "lastModifiedDateTime" : ,
    "clientState" : ,
    "expirationDateTime" : ,
    "systemCreatedAt" : ,
    "systemCreatedBy" : ,
    "systemModifiedAt" : ,
    "systemModifiedBy" :
}
```

## See Also

[Tips for working with the APIs](/dynamics365/business-central/dev-itpro/developer/devenv-connect-apps-tips)  
[subscriptions](../resources/dynamics_subscriptions.md)  
[GET subscriptions](dynamics_subscriptions_get.md)  
[DELETE subscriptions](dynamics_subscriptions_delete.md)  
[POST subscriptions](dynamics_subscriptions_create.md)  
[Business Central Dataverse API](../dynamics-dataverse-api.md)  
