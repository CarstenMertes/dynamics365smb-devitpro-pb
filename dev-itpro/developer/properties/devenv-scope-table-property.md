---
title: "Scope (Table) Property"
description: The scope property for tables sets whether the scope is cloud or on-prem in AL.
ms.custom: na
ms.date: 04/01/2021
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: reference
author: SusanneWindfeldPedersen
---

# Scope (Table) Property
> **Version**: _Available from runtime version 1.0._

Sets the scope of a table. The options are `Cloud`, `Extension`, `Internal`, `OnPrem`, and `Personalization`. 

> [!NOTE]  
> The following options `Extension`, `Internal`, and `Personalization` are being deprecated with runtime 4.0. `External` is replaced by `Cloud` and `Internal` is replaced by `OnPrem`.

## Applies to 

- Tables

## Remarks

When a table is marked with `Scope = OnPrem` it is not available to a cloud extension. System tables that have the `Scope` property set to `Internal` (`OnPrem`) cannot be accessed from extensions that have the `target` property set to `Cloud` or `External` through direct reference or through RecordRef.


## Examples

```AL
table 50105 "Retention Period"
{
    ...
    LookupPageId = "Retention Periods";
    Extensible = false;
    Scope = OnPrem;
    ...
}
```

## See Also  

[Properties](devenv-properties.md)  
[Scope Property](devenv-scope-property.md)  
[Compilation Scope Overview](../devenv-compilation-scope-overview.md)  
[JSON Files](../devenv-json-files.md)  
[Configuring Business Central Server](../../administration/configure-server-instance.md)  
