---
title: "Permission Set Object"
description: "Description of the permission set object in AL for Business Central    ."
author: SusanneWindfeldPedersen
ms.custom: na
ms.date: 01/05/2023
ms.reviewer: na
ms.topic: article
ms.author: solsen
---

# Permission Set Object

[!INCLUDE [2021_releasewave1](../includes/2021_releasewave1.md)]

The permission set object in [!INCLUDE[prod_short](includes/prod_short.md)] describes permissions on objects. Permission sets are building blocks used to compose assignable permission sets and [entitlements](devenv-entitlement-object.md). Assignable permission sets are permissions that an admin can assign to users in [!INCLUDE[prod_short](includes/prod_short.md)], using the **Permission Sets** page. An entitlement is a collection of permission sets that constitute a set of meaningful permissions for a user.

Some permission sets can be non-assignable, meaning that they aren't discoverable and assignable in the UI in [!INCLUDE[prod_short](includes/prod_short.md)], instead they can be used as building blocks to compose functional assignable permission sets.

For information about which permissions can be assigned to objects, see [Permissions on Database Objects](devenv-permissions-on-database-objects.md).

## Designing with cautiousness

If a permission set is extended through AL, the extension will make additive changes to the permission set. This behavior means an extension can provide elevated privileges to an otherwise limited set of permissions. Building permission sets that can be extended must be done carefully with this behavior in mind.

## Snippet support

Typing the shortcut `tpermissionset` will create the basic layout for a permission set object when using the [!INCLUDE[d365al_ext_md](../includes/d365al_ext_md.md)] in Visual Studio Code.

[!INCLUDE[intelli_shortcut](includes/intelli_shortcut.md)]

## Generate permission set for an object

[!INCLUDE [2022_releasewave2](../includes/2022_releasewave2.md)]

When adding new AL objects, it's easy to forget to update the permissions. With the `al.generatePermissionSetForExtensionObjects` command, you can generate or update a permission file for the active project in Visual Studio Code. Choose to create a new permission file or select an existing file to make updates to. For more information, see [AL Language Extension Configuration](devenv-al-extension-configuration.md).

## Permission set example

The following example illustrates a permission set `Sales Person` with permissions given to data in tables, each with different level of access. The [Assignable property](properties/devenv-assignable-property.md) is set to `true`, which allows the permission set to be assigned to a user. The [Permissions property](properties/devenv-permissions-property.md) is set to the list of objects to give permissions to. The `RIMD` access assigned to data in the `Customer` table provides full access, whereas, for example, access is limited for data in the `Currency` table only allowing full read and modify permission. 

> [!NOTE]  
> The name of the permissionset object is limited to 20 characters when the `Assignable` property is set to `true`. Otherwise, it's limited to 30 characters. Exceeding the limit will throw the diagnostic [Compiler Error AL0305](diagnostics/diagnostic-al305.md).

```al
permissionset 50134 "Sales Person"
{
    Assignable = true;
    Caption = 'Sales Person';

    Permissions = 
        tabledata Customer = RIMD,
        tabledata "Payment Terms" = RMD,
        tabledata Currency = RM,
        tabledata "Sales Header" = RIM,
        tabledata "Sales Line" = RIMD;
}
```

The following example of a permission set illustrates assigned permissions to run codeunits. With the [IncludedPermissionSets property](properties/devenv-includedpermissionsets-property.md), we specify that the permission set `Sales Person` is also included in `MyPermissionSet`.

```al
permissionset 50135 MyPermissionSet 
{ 
    Assignable = true;
    Caption = 'My PermissionSet';
    IncludedPermissionSets = "Sales Person"; 

    Permissions = 
        tabledata Vendor = RIm,
        codeunit SomeCode = x, 
        codeunit AccSchedManagement= X; 
} 
```

You can also use the [ExludedPermissionSets property](properties/devenv-excludedpermissionsets-property.md) to exclude permissions defined in other permission sets. To learn more, see [Composing Permission Sets From Other Permission Sets](devenv-permissionset-composing.md).

## See Also

[Developing Extensions](devenv-dev-overview.md)  
[AL Development Environment](devenv-reference-overview.md)  
[Entitlements and Permission Set Overview](devenv-entitlements-and-permissionsets-overview.md)  
[Permission Set Extension Object](devenv-permissionset-ext-object.md)  
[Permissions on Database Objects](devenv-permissions-on-database-objects.md)  
[Assignable Property](properties/devenv-assignable-property.md)  
[IncludedPermissionSets](properties/devenv-includedpermissionsets-property.md)  
[Permissions Property](properties/devenv-permissions-property.md)
