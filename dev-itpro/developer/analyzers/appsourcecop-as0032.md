---
title: "AppSourceCop Error AS0032"
description: "Controls that have been published must not be deleted, because it will break dependent extensions."
ms.author: solsen
ms.custom: na
ms.date: 01/03/2022
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# AppSourceCop Error AS0032
Controls that have been published must not be deleted.

## Description
Controls that have been published must not be deleted, because it will break dependent extensions.

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks
Removing a control which has been published is not allowed because it will break dependent extensions which are referencing or modifying it.

> [!NOTE]  
> Renaming a control will also trigger this error. AppSourceCop will consider the renamed control as a new control, unrelated to the one defined in the previous version.

## How to fix this diagnostic?

If the control was removed, revert the change by adding back the control and mark it as [Obsolete](../properties/devenv-obsoletestate-property.md).

If the control was renamed in order to change its display string in the web client, consider using the [Caption](../properties/devenv-caption-property.md) property instead.

If the control was renamed in order to comply with naming rules such as [AS0011](appsourcecop-as0011.md), consider obsoleting the control and introducing a new one.

## Examples of errors for dependent extensions

The following examples show some of the compilation errors that will be reported on dependent extensions if a control is removed from one version to another.

Version 1.0 of the extension defines a page named MyPage that contains a control named MyControl. Version 2.0 does not define this control anymore.

### Example 1 - Extensions modify this control

If a dependent extension modifies this control in a page extension or customization, when compiling against version 2.0, this will lead to a compilation error similar to `The control 'MyControl' is not found in the target 'MyPage' (AL0270)`.

```AL
pageextension 50100 SomePageExtension extends MyPage
{
    layout
    {
        modify(MyControl)
        {
            Visible = true;
        }
    }
}
```

### Example 2 - Extensions referencing this control as an anchor for a change

If a dependent extension uses this control as an anchor for a change in a page extension or customization, when compiling against version 2.0, this will lead to a compilation error similar to `The control 'MyControl' is not found in the target 'MyPage' (AL0270)`.

```AL
pageextension 50100 SomePageExtension extends MyPage
{
    layout
    {
        addafter(MyControl)
        {
            field(SomeNewControl; 15)
            {
            }
        }
    }
}
```

### Example 3 - Extensions moving this control

If a dependent extension is moving this control in a page extension or customization, when compiling against version 2.0, this will lead to a compilation error similar to `The control 'MyControl' is not found in the target 'MyPage' (AL0270)`.

```AL
pageextension 50100 SomePageExtension extends MyPage
{
    layout
    {
        movefirst(content; MyControl)
    }
}
```

## See Also  
[AppSourceCop Analyzer](appsourcecop.md)  
[Get Started with AL](../devenv-get-started.md)  
[Developing Extensions](../devenv-dev-overview.md)  
