---
title: "InherentPermissionsScope System Option"
description: "The different types of scope that the InherentPermissions attribute can apply to."
ms.author: solsen
ms.custom: na
ms.date: 12/06/2022
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# InherentPermissionsScope Option Type
> **Version**: _Available or changed with runtime version 10.0._

The different types of scope that the InherentPermissions attribute can apply to.

## Members
|  Member  |  Description  |
|----------------|---------------|
|Permissions|The Permissions scope|
|Entitlements|The Entitlements scope|
|Both|The Both scope|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

*InherentPermissionScope* is used as a parameter with InherentPermissions attribute, which can override the entitlements. It's an optional method and the default value for InherentPermissionScope is *Both* that includes permissions and entitlements. To learn more about syntax and usage of InherentPermissions attribute, see [InherentPermissions Attribute](../../attributes/devenv-inherentpermissions-attribute.md). 

## Example

```al
[InherentPermissions(PermissionObjectType:Table, Database:MyTable, 'x', InherentPermissionScope:Entitlements)]

[InherentPermissions(PermissionObjectType:Table, Database:MyTable, 'x', InherentPermissionScope:Permissions)]

[InherentPermissions(PermissionObjectType:Table, Database:MyTable, 'x', InherentPermissionScope:Both)]
```

## See Also  
[Getting Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  
[Inherent Permissions](../../devenv-inherent-permissions.md)  