---
title: Create userGroup
description: Creates a user group object in Dynamics 365 Business Central.
author: SusanneWindfeldPedersen
ms.topic: reference
ms.devlang: al
ms.date: 12/03/2023
ms.author: solsen
---

<!-- NOTE: This article is an auto-generated stub from the metadata file. -->
<!-- The sections marked with an EDIT_IS_REQUIRED require manual editing. -->
# Create userGroup

> [!NOTE]  
> User groups are replaced with [security groups](../../upgrade/deprecated-features-user-groups.md) and will be deprecated in version 25. For more information, see [security group APIs](../resources/dynamics_securitygroup.md) and [Control Access to Business Central Using Security Groups](/dynamics365/business-central/ui-security-groups).

Creates a user group in [!INCLUDE[d365fin_long_md](../../includes/d365fin_long_md.md)].

## HTTP request

Replace the URL prefix for [!INCLUDE [prod_short](../../includes/prod_short.md)] depending on environment following the [guideline](../../api-reference/v2.0/enabling-apis-for-dynamics-nav.md).

```
POST /microsoft/automation/v2.0/companies({companyId})/userGroups
```

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |
|Content-Type  |application/json|

## Request body

In the request body, supply a JSON representation of a **userGroup** object.

## Response

If successful, this method returns ```201 Created``` response code and a **userGroup** object in the response body.


## Example

**Request**

Here is an example of the request.

```json
POST https://api.businesscentral.dynamics.com/v2.0/{environment name}/api/microsoft/automation/v2.0/companies({companyId})/userGroups
Content-type: application/json
{
    "code": "NEW USER GROUP",
    "displayName": "New User Group",
    "defaultProfileID": "ACCOUNTANT"
}
```

**Response**
Here is an example of the response.
```json
HTTP/1.1 201 Created
Content-type: application/json
{
    "id": "90814d0b-caad-eb11-9b52-000d3ab03e45",
    "code": "NEW USER GROUP",
    "displayName": "New User Group",
    "defaultProfileID": "ACCOUNTANT",
    "assignToAllNewUsers": false
}
```

## See Also

[Tips for working with the APIs](../../developer/devenv-connect-apps-tips.md)  
[userGroup](../resources/dynamics_usergroup.md)  
