---
title: Create disputeStatus
description: Creates a dispute status object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen

ms.topic: reference
ms.devlang: al
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 05/31/2024
ms.author: solsen
ms.reviewer: solsen
---

<!-- NOTE: This article is an auto-generated stub from the metadata file. -->
<!-- The sections marked with an EDIT_IS_REQUIRED require manual editing. -->
# Create disputeStatus

Creates a dispute status in [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request

Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).
<!-- START>EDIT_IS_REQUIRED. There URL for accessing the endpoint might be different or there might be more than one -->
```
POST businesscentralPrefix/companies({id})/disputeStatus({id})
```
<!-- END>EDIT_IS_REQUIRED -->
## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |
|Content-Type  |application/json|

## Request body

In the request body, supply a JSON representation of a **disputeStatus** object.

## Response

If successful, this method returns ```201 Created``` response code and a **disputeStatus** object in the response body.


## Example

**Request**

Here's an example of the request.
<!-- START>EDIT_IS_REQUIRED. There URL for accessing the endpoint might be different. Fill in the property values -->
```json
POST https://{businesscentralPrefix}/api/v2.0/companies({id})/disputeStatus({id})
Content-type: application/json
{
    "id" : "",
    "code" : "",
    "displayName" : ""
}
```
<!-- END>EDIT_IS_REQUIRED -->
**Response**

Here's an example of the response.
<!-- START>EDIT_IS_REQUIRED. Fill in values for properties -->
```json
HTTP/1.1 201 Created
Content-type: application/json
{
    "id" : "",
    "code" : "",
    "displayName" : ""
}
```
<!-- END>EDIT_IS_REQUIRED -->
## Related information

[Tips for working with the APIs](/dynamics365/business-central/dev-itpro/developer/devenv-connect-apps-tips)  
[disputeStatus](../resources/dynamics_disputeStatus.md)  
[GET disputeStatus](dynamics_disputestatus_get.md)  
[DELETE disputeStatus](dynamics_disputestatus_delete.md)  
[PATCH disputeStatus](dynamics_disputestatus_update.md)  
