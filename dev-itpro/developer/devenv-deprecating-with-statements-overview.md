---
title: "Deprecating Explicit and Implicit With Statements"
description: "Rationale and description of why explicit and implicit with statements are deprecated in AL"
ms.custom: na
ms.date: 08/15/2022
ms.reviewer: solsen
ms.topic: overview
author: esbenk
---

# Deprecating Explicit and Implicit With Statements

[!INCLUDE[2020_releasewave2](../includes/2020_releasewave2.md)]

> [!NOTE]  
> With [!INCLUDE[prod_short](../includes/prod_short.md)] 2022 release wave 2, the **AL:Go!** template for creating new AL projects in Visual Studio Code, now enables explicit `with` statements by default, by adding the `NoImplicitWith` option to the `features` property in the generated app.json file.

The extensibility model and the AL programming language are successors to the C/AL language. And the `with` statement has up until now been supported in AL. While using the `with` statement might make code harder to read, it can also prevent code in [!INCLUDE[prod_short](includes/prod_short.md)] online from being upgraded without changes to the code or even worse - upgraded, but with changed behavior. We distinguish between two types of with statements; the explicit type of `with` using the keyword, and the implicit with which isn't expressed directly in code. The next sections describe the explicit and implicit types one by one.

## The explicit with statement

In [!INCLUDE[prod_short](includes/prod_short.md)] online your code is recompiled when the platform and application versions are upgraded. The recompilation ensures that it's working and the recompile regenerates the runtime artifacts to match the new platform. Breaking changes without due warning aren't allowed, but the use of the `with` statement makes it impossible, as Microsoft, to make even additive changes in a non-breaking way. This problem isn't alone isolated to changes made by Microsoft; any additive change has the potential to break a `with` statement in consuming code.

The following example illustrates code written using the `with` statement; referred to in this context as the explicit `with`.

```AL
codeunit 50140 MyCodeunit
{
    procedure DoStuff()
    var
        Customer: Record Customer;
    begin
        with Customer do begin
            // Do some work on the Customer record.
            Name := 'Foo';

            if IsDirty() then 
                Modify();
        end;
    end; 

    local procedure IsDirty(): Boolean;
    begin
        exit(false);
    end;
}
```

The `DoStuff()` procedure processes work on the Customer record and calls a local procedure `IsDirty()` to check whether to update the record or not. Looking at the code above it looks like it does nothing since `IsDirty()` returns `false` - assuming that the `IsDirty()` call (line 11) is in fact calling the local `IsDirty()` procedure.

## Symbol lookup

If we take another look at the above code sample again, what would happen to that code if `IsDirty` was added to the base application between two releases? To understand that we need to take a look at how compilers turn syntax into symbols. When the AL compiler meets the `IsDirty` call it must bind the syntax name to a procedure symbol.

When the AL compiler searches for the symbol `IsDirty()` in the sample above it will search in following order:

1. Customer table
    - User-defined members on the Customer table and Customer table extensions
    - Platform-defined members, for example, `FindFirst()` or `Modify()`
2. MyCodeunit codeunit
    - User-defined members, for example, `IsDirty()`
    - Platform-defined members
3. Globally defined members

The first time the search for `IsDirty` finds the name IsDirty, it will not continue to the next top-level group. That means that if a procedure named `IsDirty` is introduced in the Customer table (platform or application) that procedure will be found instead of the procedure in `MyCodeunit`.

The solution for the *explicit* `with` is to stop using it. Using the `with` statement can make your code vulnerable to upstream changes. The example below illustrates how to rewrite the sample in [The explicit with statement](devenv-deprecating-with-statements-overview.md#the-explicit-with-statement):

```AL 
// Safe version
codeunit 50140 MyCodeunit
{
    procedure DoStuff()
    var
        Customer: Record Customer;
    begin
        // Do some work on the Customer record.
        Customer.Name := 'Foo';

        if IsDirty() then 
            Customer.Modify();
    end; 

    local procedure IsDirty(): Boolean;
    begin
        exit(false);
    end;
} 
```

## The implicit with statement

The implicit `with` is injected automatically by the compiler in certain situations. The next sections describe, how it works on codeunits and pages.

### Codeunits

When a codeunit has the `TableNo` property set, there's an implicit `with` around the code inside the `OnRun` trigger. The implicit `with` is indicated with the comments in the code example below.

```AL
codeunit 50140 MyCodeunit
{
    TableNo = Customer;

    trigger OnRun()
    begin
        // with Rec do begin
        SetRange("No.", '10000', '20000');
        if Find() then
            repeat
            until Next() = 0;

        if IsDirty() then
            Error('Something is not clean');
        // end;
    end;

    local procedure IsDirty(): Boolean;
    begin
        exit(false);
    end;
}
```

Similar to the [The explicit with statement](devenv-deprecating-with-statements-overview.md#the-explicit-with-statement), the code looks like it will call the local `IsDirty` method, but depending on the Customer table, extensions to the Customer table, and built-in methods that may not be the case. If any of these implement an `IsDirty` method with an identical signature that returns `true`, then the example above will fail with an error. If an `IsDirty` method with a different signature is implemented, then this code won't compile and will fail to upgrade.

## Pages

Pages on tables have the same type of implicit with, but around the entire object. Everywhere inside the page object the fields and methods from the source tables are directly available without any prefix.

```AL
page 50143 ImplicitWith
{
    SourceTable = Customer;

    layout
    {
        area(Content)
        {
            field("No."; "No.") { }
            field(Name; Name)
            {
                trigger OnValidate()
                begin
                    Name := 'test';
                end;
            }
        }
    }

    trigger OnInit()
    begin
        if IsDirty() then Insert()
    end;

    local procedure IsDirty(): Boolean
    begin
        exit(Name <> '');
    end;
}
```

On pages, it's not only the code in triggers and procedures that is spanned by the implicit with on the source `Rec`; also the source expressions for the fields are covered.

## Warnings and using pragma

From [!INCLUDE[prod_short](includes/prod_short.md)] 2020 release wave 2 we begin to warn about the use of explicit and implicit with for extensions that are targeting the cloud. There are two different warnings: `AL0604` and `AL0606`.

> [!NOTE]  
> The warnings will become errors with a future release. We will at the earliest remove with statement support from the [!INCLUDE[prod_short](includes/prod_short.md)] 2021 release wave 2.

### AL0606 - use of explicit with

The warning has a Quick Fix code action that allows you to convert the statement(s) inside the `with` statement to fully qualified statements, which means statements as shown in [The explicit with statement](devenv-deprecating-with-statements-overview.md#the-explicit-with-statement).

### AL0604 - use of implicit with

Just qualifying with `Rec.` won't solve this problem. The `IsDirty()` will still be vulnerable to upstream change. We want to remove the implicit with, but also offer an opt-in model to avoid forcing everyone to upgrade their code at once.

The solution for that is to introduce pragmas in AL. A pragma is an instruction to the compiler on how it should understand the code. The pragma instructs the compiler not to create an implicit with for the `Rec` variable.

The following shows the syntax for the implicit with pragma. The pragma must be used before the beginning of the codeunit or page. For more information, see [Pragma Directive](directives/devenv-directive-pragma.md) and [Pragma ImplicitWith](directives/devenv-directive-pragma-implicitwith.md).

```AL
#pragma implicitwith disable|restore
```

The fixed example under [Pages](devenv-deprecating-with-statements-overview.md#pages) will then look like this:

```AL
#pragma implicitwith disable
page 50143 ImplicitWith
{
    SourceTable = Customer;

    layout
    {
        area(Content)
        {
            field("No."; Rec."No.") { }
            field(Name; Rec.Name)
            {
                trigger OnValidate()
                begin
                    Rec.Name := 'test';
                end;
            }
        }
    }

    trigger OnInit()
    begin
        if IsDirty() then Rec.Insert()
    end;

    local procedure IsDirty(): Boolean
    begin
        exit(Name <> '');
    end;
} 
#pragma implicitwith restore
```

The Quick Fix code actions will automatically insert the pragma before and after the fixed object. 

> [!TIP]  
> Remember to **Enable Code Actions** in the settings for the AL Language extension. For more information, see [Code Actions](devenv-code-actions.md).

In the `app.json` file, you can set the `NoImplicitWith` flag to disable implicit with when you've rewritten all code. For more information, see [JSON Files](devenv-json-files.md#appjson-file).

## Suppressing warnings 

There are two ways of suppressing warnings to unclutter warnings while working on other issues and then afterwards you can fix the warnings at your own pace.

### suppressWarnings setting

Warnings can be suppressed globally in an extension by specifying the `suppressWarnings` in the `app.json` file. For more information, see [AL Language Extension Configuration](devenv-al-extension-configuration.md). The syntax is:

```json
"suppressWarnings": [ "AL0606", "AL0604" ]
```

### Pragmas

It's also possible to use `#pragma` to suppress individual warnings for one or more lines of code. For more information, see [Pragma Warning](directives/devenv-directive-pragma-warning.md).

```AL
#pragma warning disable AL0606
    // No AL0606 will be shown for code here.
    with Customer do begin
        Name := 'Foo';
        Insert();
    end;

#pragma warning restore AL0606
// Suppression of AL0606 is restored to global state.
```


## See Also

[AL Development Environment](devenv-reference-overview.md)  
[Developing Extensions in AL](devenv-dev-overview.md)  
[Directives in AL](directives/devenv-directives-in-al.md)  
[Pragma Directive](directives/devenv-directive-pragma.md)  
[Pragma ImplicitWith](directives/devenv-directive-pragma-implicitwith.md)  
[Pragma Warning](directives/devenv-directive-pragma-warning.md)  
[Best Practices for Deprecation of Code in the Base App](devenv-deprecation-guidelines.md)  
[Microsoft Timeline for Deprecating Code in Business Central](devenv-deprecation-timeline.md)  
[AL Simple Statements](devenv-al-simple-statements.md)