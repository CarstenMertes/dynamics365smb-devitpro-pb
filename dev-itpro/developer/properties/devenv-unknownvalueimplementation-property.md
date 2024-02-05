---
title: "UnknownValueImplementation Property"
description: "Specifies the implementers used for ordinal values that are not included in the defined list of enum values."
ms.author: solsen
ms.custom: na
ms.date: 06/15/2022
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# UnknownValueImplementation Property
> **Version**: _Available or changed with runtime version 7.0._

Specifies the implementers used for ordinal values that are not included in the defined list of enum values.

## Applies to
-   Enum Type

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Syntax

```al
UnknownValueImplementation = Interface = InterfaceImplementation;

```

## Example

The following example illustrates different implementations of the `IFoo` interface. `SomeEnum` has `UnknownValueImplementation` set to catch the case where some extension uses an unknown enum value.


```al
pageextension 50130 CustListExt extends "Customer List"
{

    trigger OnOpenPage()
    var
        ifoo: Interface IFoo;
        e: enum SomeEnum;
    begin
        e := SomeEnum::Yes;
        ifoo := e;
        ifoo.Foo(); // => YesFooImpl specified in Implementation on Yes value

        e := SomeEnum::No;
        ifoo := e;
        ifoo.Foo(); // => DefaultFooImpl specified in DefaultImplementation

        e := 2; // No enum value matches this.
        ifoo := e;
        ifoo.Foo(); // => UnknownFooImpl specified in UnknownImplementation
    end;
}

interface IFoo
{
    procedure Foo();
}

codeunit 50145 ErrorFooImpl implements IFoo
{
    procedure Foo()
    begin
        Message('Bad FOO')
    end;
}

codeunit 50146 DefaultFooImpl implements IFoo
{
    procedure Foo()
    begin
        Message('Default FOO')
    end;
}

codeunit 50147 YesFooImpl implements IFoo
{
    procedure Foo()
    begin
        Message('Yes FOO')
    end;
}

enum 50135 SomeEnum implements IFoo
{
    Extensible = true;
    UnknownValueImplementation = IFoo = ErrorFooImpl;
    DefaultImplementation = IFoo = DefaultFooImpl;

    value(0; Yes)
    {
        Implementation = IFoo = YesFooImpl;
    }
    value(1; No)
    {
        // Nothing specified. Using defaults
    }
}
```

## Remarks

The `UnknownValueImplementation` property applies to enums. Uninstalling enum extensions can result in persisted values becoming unknown. The `UnknownValueImplementation` provides a generic error handling in such cases. Enums are often used to select an interface implementation. However, due to the nature of an extensible development model, an enum extension and its corresponding interface implementation can be uninstalled from a tenant, while the value for the specific enum is still available, but now pointing to an unknown value. Using the `UnknownValueImplementation` property when defining an enum prevents throwing a technical error message in the UI and allows for a more user-friendly error handling.

Related to `UnknownValueImplementation` is the `DefaultImplementation` property, used for fallback to a default value when no enum value is provided. For more information, see [DefaultImplementation Property](devenv-defaultimplementation-property.md).


## See Also

[DefaultImplementation Property](devenv-defaultimplementation-property.md)  
[Get Started with AL](../devenv-get-started.md)  
[Developing Extensions](../devenv-dev-overview.md)  