---
title: Get userPermission | Microsoft Docs
description: Gets userPermission objects in Dynamics 365 Business Central.
documentationcenter: ''
author: henrikwh

ms.topic: reference
ms.devlang: na
ms.workload: na
ms.date: 10/01/2020
ms.author: solsen
---

# Get userGroupMembers
Retrieves the properties and relationships of an userGroupMembers object for [!INCLUDE[d365fin_long_md](../developer/includes/d365fin_long_md.md)].

## HTTP request
```
GET /microsoft/automation/{apiVersion}/companies({companyId})/users({userSecurityID})/userPermissions
```

## Request headers
|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |

## Request body
Do not supply a request body for this method.

## Response
If successful, this method returns a ```200 OK``` response code and list of  **userPermission** objects in the response body.

## Example

**Request**

Here is an example of the request.
```json
GET https://api.businesscentral.dynamics.com/v2.0/{environment name}/api/microsoft/automation/v1.0/companies({companyId})/users({userSecurityID})/userPermissions
```

**Response**

Here is an example of the response. 

> [!NOTE]  
>   The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```json
{
    "userSecurityID": "a0ad6d24-99b7-440e-a26d-9a86840c2056",
    "id": "SUPER",
    "company": "",
    "scope": "System",
    "appId": "00001111-aaaa-2222-bbbb-3333cccc4444",
    "displayName": "This role has all permissions.",
    "extensionName": ""

}
```

## See Also 
[Introduction to Automation APIs](itpro-introduction-to-automation-apis.md)  
[UserPermission Resource Type](dynamics-microsoft-automation-userpermission.md)  
