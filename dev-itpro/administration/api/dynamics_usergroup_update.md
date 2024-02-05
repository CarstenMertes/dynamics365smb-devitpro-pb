---
title: Update userGroup
description: Updates an  user group object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 12/03/2023
ms.author: solsen
---

<!-- NOTE: This article is an auto-generated stub from the metadata file. -->
<!-- The sections marked with an EDIT_IS_REQUIRED require manual editing. -->
# Update userGroup

> [!NOTE]  
> User groups are replaced with [security groups](../../upgrade/deprecated-features-user-groups.md) and will be deprecated in version 25. For more information, see [security group APIs](../resources/dynamics_securitygroup.md) and [Control Access to Business Central Using Security Groups](/dynamics365/business-central/ui-security-groups).

Updates the properties of an user group object for [!INCLUDE[d365fin_long_md](../../includes/d365fin_long_md.md)].

## HTTP request

Replace the URL prefix for [!INCLUDE [prod_short](../../includes/prod_short.md)] depending on environment following the [guideline](../../api-reference/v2.0/enabling-apis-for-dynamics-nav.md).

```
PATCH /microsoft/automation/v2.0/companies({companyId})/userGroups({userGroupId})
```

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |
|Content-Type  |application/json|
|If-Match      |Required. When this request header is included and the eTag provided does not match the current tag on the **userGroup**, the **user group** will not be updated. |

## Request body

In the request body, supply the values for relevant fields that should be updated. Existing properties that are not included in the request body will maintain their previous values or be recalculated based on changes to other property values. For best performance you shouldn't include existing values that haven't changed.

## Response

If successful, this method returns a ```200 OK``` response code and an updated **userGroup** object in the response body.

## Example

**Request**

Here is an example of the request.
<!-- START>EDIT_IS_REQUIRED. There URL for accessing the endpoint might be different. Fill in the property values)-->

```json
PATCH https:///microsoft/automation/{apiVersion}/companies({companyId})/userGroups({userGroupId})
Content-type: application/json
{
    "displayName" : "YourUserGroupName"
}
```

**Response**
Here is an example of the response.

```json
HTTP/1.1 200 OK
Content-type: application/json
{
    "id": "d38a92e2-9d74-eb11-bb5c-00155df3a615",
    "code": "D365 ACCOUNTANTS",
    "displayName": "YourUserGroupName",
    "defaultProfileID": "ACCOUNTANT PORTAL",
    "assignToAllNewUsers": false
}
```

## See Also

[Tips for working with the APIs](../../developer/devenv-connect-apps-tips.md)  
[userGroup](../resources/dynamics_userGroup.md)