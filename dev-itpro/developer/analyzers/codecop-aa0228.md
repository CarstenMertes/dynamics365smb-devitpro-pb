---
title: "CodeCop Warning AA0228"
description: "The local method must be used, otherwise the variable is not necessary."
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
# CodeCop Warning AA0228
The local method must be used; otherwise removed.

## Description
The local method must be used, otherwise the variable is not necessary.

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Reason for the rule
Unused methods can be confusing for the reader and can cost performance to the system. 

## Bad code example
```AL
codeunit 10 MyCodeunit
{
    var
       RenameErr: Label 'You cannot rename';

    local procedure Method1()
    begin
       Message(RenameErr);
    end;
 
    procedure Method2()
    begin
       Error(RenameErr);
    end;
}
```

## Good code example
```AL
codeunit 10 MyCodeunit
{
    var
       RenameErr: Label 'You cannot rename';

    procedure Method2()
    begin
       Error(RenameErr);
    end;
}
```

## Good and bad practices for fixing the rule
Remove the unused local method from the code.

## See Also  
[CodeCop Analyzer](codecop.md)  
[Get Started with AL](../devenv-get-started.md)  
[Developing Extensions](../devenv-dev-overview.md)  