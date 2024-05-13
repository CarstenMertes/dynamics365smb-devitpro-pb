---
title: Update userGroupMember
description: Updates an  user group member object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 04/01/2021
ms.author: solsen
---

<!-- NOTE: This article is an auto-generated stub from the metadata file. -->
<!-- The sections marked with an EDIT_IS_REQUIRED require manual editing. -->
# Update userGroupMember

Updates the properties of an user group member object for [!INCLUDE[d365fin_long_md](../../includes/d365fin_long_md.md)].

## HTTP request

Replace the URL prefix for [!INCLUDE [prod_short](../../includes/prod_short.md)] depending on environment following the [guideline](../../api-reference/v2.0/enabling-apis-for-dynamics-nav.md).


```
PATCH /microsoft/automation/v2.0/companies({companyId})/users({userSecurityId})/userGroupMembers({userGroupMemberId})
```

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |
|Content-Type  |application/json|
|If-Match      |Required. When this request header is included and the eTag provided does not match the current tag on the **userGroupMember**, the **user group member** will not be updated. |

## Request body

In the request body, supply the values for relevant fields that should be updated. Existing properties that are not included in the request body will maintain their previous values or be recalculated based on changes to other property values. For best performance you shouldn't include existing values that haven't changed.

## Response

If successful, this method returns a ```200 OK``` response code and an updated **userGroupMember ** object in the response body.

## Example

**Request**

Here is an example of the request.

```json
PATCH https://api.businesscentral.dynamics.com/v2.0/{environment name}/api/microsoft/automation/v2.0/companies({companyId})/users({userSecurityId})/userGroupMembers({userGroupMemberId})

Content-type: application/json
{
    "displayName": "YourDisplayName"
}
```

**Response**
Here is an example of the response.


```json
HTTP/1.1 200 OK
Content-type: application/json
{
    "id": "d38a92e2-9d74-eb11-bb5c-00155df3a615",
    "code": "D365 BUS PREMIUM",
    "userSecurityId": "7ae30772-481f-4895-a042-98f36e280680",
    "companyName": "CRONUS USA, Inc.",
    "displayName": "YourDisplayName"
}
```

## See Also

[Tips for working with the APIs](../../developer/devenv-connect-apps-tips.md)  
[userGroupMember](../resources/dynamics_userGroupMember.md)