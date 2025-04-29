---
title: Get externaleventsubscriptions
description: Gets an externaleventsubscriptions object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.service: "dynamics365-business-central"
ms.topic: reference
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 04/28/2025
ms.author: solsen
---

<!-- NOTE: This article is an auto-generated stub from the metadata file. -->
<!-- The sections marked with an EDIT_IS_REQUIRED require manual editing. -->
# Get externaleventsubscriptions

Retrieves the properties and relationships of an externaleventsubscriptions object for [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request

Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).
<!-- START>EDIT_IS_REQUIRED. There URL for accessing the endpoint might be different -->
```
GET businesscentralPrefix/companies({id})/externaleventsubscriptions({id})
```
<!-- END>EDIT_IS_REQUIRED -->
## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a ```200 OK``` response code and an **externaleventsubscriptions** object in the response body.

## Example

**Request**

Here's an example of the request.
<!-- START>EDIT_IS_REQUIRED. There URL for accessing the endpoint might be different -->
```json
GET https://{businesscentralPrefix}/api/v2.0/companies({id})/externaleventsubscriptions({id})
```
<!-- END>EDIT_IS_REQUIRED -->
**Response**

Here's an example of the response.

<!-- START>EDIT_IS_REQUIRED. Fill in values for properties -->
```json
{
    "id" : "",
    "companyId" : "",
    "timestamp" : "",
    "appId" : "",
    "eventName" : "",
    "companyName" : "",
    "userId" : "",
    "notificationUrl" : "",
    "lastModifiedDateTime" : "",
    "clientState" : "",
    "subscriptionType" : "",
    "eventVersion" : "",
    "subscriptionState" : "",
    "systemCreatedAt" : "",
    "systemCreatedBy" : "",
    "systemModifiedAt" : "",
    "systemModifiedBy" : ""
}
```
<!-- END>EDIT_IS_REQUIRED -->
## Related information

[Tips for working with the APIs](/dynamics365/business-central/dev-itpro/developer/devenv-connect-apps-tips)  
[externaleventsubscriptions](../resources/dynamics_externaleventsubscriptions.md)  
[DELETE externaleventsubscriptions](dynamics_externaleventsubscriptions_delete.md)  
[POST externaleventsubscriptions](dynamics_externaleventsubscriptions_create.md)  
[PATCH externaleventsubscriptions](dynamics_externaleventsubscriptions_update.md)  
