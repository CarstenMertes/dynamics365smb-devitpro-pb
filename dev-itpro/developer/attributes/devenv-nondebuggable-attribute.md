---
title: "NonDebuggable Attribute"
description: "Specifies that the annotated symbol will not be available to the debugger."
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

# NonDebuggable Attribute
> **Version**: _Available or changed with runtime version 2.0._

Specifies that the annotated symbol will not be available to the debugger. E.g. methods can't be stepped through and variables can't be inspected.


## Applies To

- Variable
- Method


## Syntax

```AL
[NonDebuggable]
```

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Example
Setting the attribute on a method. Each method must be marked with `[NonDebuggable]`.

```AL
codeunit 50142 NoDebuggingOfMethod
{
    [NonDebuggable]
    local procedure MyProcedure()
    var
        myInt: Integer;
    begin
        //Make something happen
    end;
}

```

Setting the attribute on variables. Each variable must be marked as `[NonDebuggable]`.
```AL
codeunit 50143 NoDebuggingOfVar 
{
    local procedure MyProcedure()
    var
        [NonDebuggable]
        myInt: Integer;
    begin
        //Make something happen
    end;
}

```

## Remarks

Regardless of the resource exposure policy setting, methods and variables marked with the `[NonDebuggable]` attribute, will remain non-debuggable. For more information, see [Resource Exposure Policy Setting](../devenv-security-settings-and-ip-protection.md).
  
## See Also  

[AL Method Reference](../methods-auto/library.md)  
[Debugging](../devenv-debugging.md)