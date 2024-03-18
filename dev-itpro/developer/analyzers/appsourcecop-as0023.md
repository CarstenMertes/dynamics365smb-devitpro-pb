---
title: "AppSourceCop Error AS0023"
description: "A return type cannot be modified in external procedures."
ms.author: solsen
ms.custom: na
ms.date: 12/07/2021
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# AppSourceCop Error AS0023
A return type cannot be modified in external procedures

## Description
A return type cannot be modified in external procedures.

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

This rule validates that the return type of a public procedure has not been changed in a way that would break the compilation of dependent extensions.
It is not allowed to change the return type of a public procedure that was published with a return type in a previous version.
Adding a return type is allowed by this rule, but is validated by [AS0102](appsourcecop-as0102.md).

> [!NOTE]  
> This rule also covers the cases related to the [TryFunction](/dynamics365/business-central/dev-itpro/developer/attributes/devenv-tryfunction-attribute) attribute which implicitly defines a Boolean return type. 

## How to fix this diagnostic?

Reverting the change will fix this diagnostic. If changing the return type is required, the recommended approach is to mark the procedure with the [Obsolete](../attributes/devenv-obsolete-attribute.md) attribute and introduce a new one with the desired return type. In a future version, once all dependent extensions have updated their code to not reference the obsolete procedure, you can remove it.

## Code examples triggering the rule

In the following examples, version 1.0 of the extension defines a public procedure which returns an Integer.

Version 1.0 of the extension:
```AL
codeunit 50100 MyCodeunit
{
    procedure MyProcedure(): Integer
    begin
        exit(5);
    end;
}
```

### Example 1 - Changing the return type of a procedure from Integer to Boolean

Version 2.0 of the extension:
```AL
codeunit 50100 MyCodeunit
{
    procedure MyProcedure(): Boolean
    begin
        exit(true);
    end;
}
```

In version 2.0, the return type of `MyProcedure` has changed from `Integer` to `Boolean`. If a dependent extension used the return type of this procedure, this will lead to a compilation error similar to `Cannot implicitly convert type 'Boolean' to 'Integer' (AL0122)`.

For example, the following extension compiles when depending on version 1.0, but fails to compile with version 2.0:
```AL
codeunit 50120 AnotherCodeunit
{
    procedure AnotherMethod()
    var
        c: Codeunit MyCodeunit;
        myInt: Integer;
    begin
        myInt := c.MyProcedure();
    end;
}
```

### Example 2 - Removing the return type of a procedure

Version 2.0 of the extension:
```AL
codeunit 50100 MyCodeunit
{
    procedure MyProcedure()
    begin
    end;
}
```

In version 2.0, the procedure does not return anything anymore. If a dependent extension used the return type of this procedure, this will lead to a compilation error similar to `Cannot implicitly convert type 'None' to 'Integer' (AL0122)`.

For example, the following extension compiles when depending on version 1.0, but fails to compile with version 2.0:
```AL
codeunit 50120 AnotherCodeunit
{
    procedure AnotherMethod()
    var
        c: Codeunit MyCodeunit;
        myInt: Integer;
    begin
        myInt := c.MyProcedure();
    end;
}
```

### Example 3 - Removing the return type of a procedure and adding a TryFunction attribute

Version 2.0 of the extension:
```AL
codeunit 50100 MyCodeunit
{
    [TryFunction]
    procedure MyProcedure()
    begin
        exit(true);
    end;
}
```

In version 2.0, the procedure now returns a Boolean value because it is marked as a TryFunction. This scenario would lead to the same compilation errors than mentioned in Example 1 above.

## Code examples not triggering the rule

In the following examples, the version 1.0 of the extension defines a procedure which does not have a return type.

Version 1.0 of the extension:
```AL
codeunit 50100 MyCodeunit
{
    procedure MyProcedure()
    begin
    end;
}
```

### Example 1 - Adding a return type to a procedure

Version 2.0 of the extension:
```AL
codeunit 50100 MyCodeunit
{
    procedure MyProcedure(): Boolean
    begin
        exit(true);
    end;
}
```

In version 2.0, the procedure `MyProcedure` is now returning a boolean. However, it does not break the compilation of dependent extensions because they were not consuming the return type of the procedure.

> [!IMPORTANT]  
> Adding a return type to a procedure is a runtime breaking changes. Dependent extensions that are referencing the procedure must be recompiled in order to avoid experiencing issues at runtime. For on-premises installations this can be done using [Repair-NavApp](/powershell/module/microsoft.dynamics.nav.apps.management/repair-navapp). For SaaS, we do not allow adding return types, this is validated by the rule [AS0102](appsourcecop-as0102.md).

### Example 2 - Adding a TryFunction attribute to a procedure

Version 2.0 of the extension:
```AL
codeunit 50100 MyCodeunit
{
    [TryFunction]
    procedure MyProcedure()
    begin
        exit(true);
    end;
}
```

In version 2.0, the procedure is now marked as a TryFunction. This means that this return type has implicitly been changed to Boolean. Similarly, it is possible to add a TryFunction attribute on a function that already returned a Boolean.

## See Also  
[AppSourceCop Analyzer](appsourcecop.md)  
[Get Started with AL](../devenv-get-started.md)  
[Developing Extensions](../devenv-dev-overview.md)
