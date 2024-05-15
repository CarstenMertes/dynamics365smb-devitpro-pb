---
title: "Assignable Property"
description: "Sets whether the permission set can be assigned to a user."
ms.author: solsen
ms.date: 02/26/2024
ms.tgt_pltfrm: na
ms.topic: reference
author: SusanneWindfeldPedersen
ms.reviewer: solsen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Assignable Property
> **Version**: _Available or changed with runtime version 7.0._

Sets whether the permission set can be assigned to a user.

## Applies to
-   Permission Set

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Syntax

```al
permissionset 50100 MyPermissionSet
{
    Assignable = true;
...
```

## Remarks

Assignable permission sets are permissions that an admin can assign to users in [!INCLUDE[prod_short](../../includes/prod_short.md)], using the **Permission Sets** page.

## See Also  

[Get Started with AL](../devenv-get-started.md)  
[Developing Extensions](../devenv-dev-overview.md)  
[PermissionSet Object](../devenv-permissionset-object.md)  
[PermissionSet Extension Object](../devenv-permissionset-ext-object.md)  