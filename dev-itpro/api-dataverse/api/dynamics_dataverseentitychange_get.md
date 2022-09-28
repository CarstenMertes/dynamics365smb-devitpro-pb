---
title: Get dataverseEntityChanges
description: Gets a dataverse entity change object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.service: "dynamics365-business-central"
ms.topic: reference
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 08/25/2022
ms.author: solsen
---

<!-- NOTE: This article is an auto-generated stub from the metadata file. -->
<!-- The sections marked with an EDIT_IS_REQUIRED require manual editing. -->
# Get dataverseEntityChanges

Retrieves the properties and relationships of a dataverse entity change object for [!INCLUDE [prod_short](../../includes/prod_short.md)].

## HTTP request

Replace the URL prefix for [!INCLUDE [prod_short](../../includes/prod_short.md)] depending on environment following the [guideline](../../api-reference/v2.0/endpoints-apis-for-dynamics.md).

```
GET businesscentralPrefix/companies({id})/dataverseEntityChanges({id})
```

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |

## Request body

Do not supply a request body for this method.

## Response

If successful, this method returns a ```200 OK``` response code and a **dataverseEntityChange** object in the response body.

## Example

**Request**

Here is an example of the request.

```json
GET https://{businesscentralPrefix}/api/v2.0/companies({id})/dataverseEntityChanges({id})
```

**Response**

Here is an example of the response.


```json
{
    "id" : "",
    "entityName" : ""
}
```

## See Also

[Tips for working with the APIs](/dynamics365/business-central/dev-itpro/developer/devenv-connect-apps-tips)  
[dataverseEntityChange](../resources/dynamics_dataverseEntityChange.md)  
[POST dataverseEntityChange](dynamics_dataverseentitychange_create.md)  
[Business Central Dataverse API](../dynamics-dataverse-api.md)  
