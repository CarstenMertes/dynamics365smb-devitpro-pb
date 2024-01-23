---
title: Create dataverseEntityChanges
description: Creates a dataverse entity change object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.service: "dynamics365-business-central"
ms.topic: reference
ms.devlang: al
ms.date: 08/25/2022
ms.author: solsen
---

<!-- NOTE: This article is an auto-generated stub from the metadata file. -->
<!-- The sections marked with an EDIT_IS_REQUIRED require manual editing. -->
# Create dataverseEntityChanges

Creates a dataverse entity change in [!INCLUDE [prod_short](../../includes/prod_short.md)].

## HTTP request

Replace the URL prefix for [!INCLUDE [prod_short](../../includes/prod_short.md)] depending on environment following the [guideline](../../api-reference/v2.0/endpoints-apis-for-dynamics.md).

```
POST businesscentralPrefix/companies({id})/dataverseEntityChanges({id})
```

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |
|Content-Type  |application/json|
|If-Match      |Required. When this request header is included and the eTag provided does not match the current tag on the **dataverseEntityChange**, the **dataverseEntityChange** will not be updated. |

## Request body

In the request body, supply a JSON representation of a **dataverseEntityChange** object.

## Response

If successful, this method returns ```201 Created``` response code and a **dataverseEntityChange** object in the response body.


## Example

**Request**

Here is an example of the request.

```json
POST https://{businesscentralPrefix}/api/v2.0/companies({id})/dataverseEntityChanges({id})
Content-type: application/json
{
    "id" : "",
    "entityName" : ""
}
```

**Response**

Here is an example of the response.

```json
HTTP/1.1 201 Created
Content-type: application/json
{
    "id" : "",
    "entityName" : ""
}
```

## See Also

[Tips for working with the APIs](/dynamics365/business-central/dev-itpro/developer/devenv-connect-apps-tips)  
[dataverseEntityChange](../resources/dynamics_dataverseEntityChange.md)  
[GET dataverseEntityChange](dynamics_dataverseentitychange_get.md)  
[Business Central Dataverse API](../dynamics-dataverse-api.md)  
