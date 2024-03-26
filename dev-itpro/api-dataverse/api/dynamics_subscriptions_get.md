---
title: Get subscriptions
description: Gets a subscriptions object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 08/25/2022
ms.author: solsen
---

<!-- NOTE: This article is an auto-generated stub from the metadata file. -->
<!-- The sections marked with an EDIT_IS_REQUIRED require manual editing. -->
# Get subscriptions

Retrieves the properties and relationships of a subscriptions object for [!INCLUDE [prod_short](../../includes/prod_short.md)].

## HTTP request

Replace the URL prefix for [!INCLUDE [prod_short](../../includes/prod_short.md)] depending on environment following the [guideline](../../api-reference/v2.0/endpoints-apis-for-dynamics.md).

```
GET businesscentralPrefix/companies({id})/subscriptions({id})
```

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |

## Request body

Do not supply a request body for this method.

## Response

If successful, this method returns a ```200 OK``` response code and a **subscriptions** object in the response body.

## Example

**Request**

Here is an example of the request.

```json
GET https://{businesscentralPrefix}/api/v2.0/companies({id})/subscriptions({id})
```

**Response**

Here is an example of the response.


```json
{
    "subscriptionId" : "",
    "notificationUrl" : "",
    "resource" : "",
    "timestamp" : "",
    "userId" : "",
    "lastModifiedDateTime" : "",
    "clientState" : "",
    "expirationDateTime" : "",
    "systemCreatedAt" : "",
    "systemCreatedBy" : "",
    "systemModifiedAt" : "",
    "systemModifiedBy" : ""
}
```

## See Also

[Tips for working with the APIs](/dynamics365/business-central/dev-itpro/developer/devenv-connect-apps-tips)  
[subscriptions](../resources/dynamics_subscriptions.md)  
[DELETE subscriptions](dynamics_subscriptions_delete.md)  
[POST subscriptions](dynamics_subscriptions_create.md)  
[PATCH subscriptions](dynamics_subscriptions_update.md)  
[Business Central Dataverse API](../dynamics-dataverse-api.md)  
