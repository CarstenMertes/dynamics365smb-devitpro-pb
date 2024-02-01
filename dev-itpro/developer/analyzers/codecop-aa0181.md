---
title: "CodeCop Warning AA0181"
description: "Avoid getting the dataset when an enumeration is not used, which will decrease performance."
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
# CodeCop Warning AA0181
The FindSet() or Find() methods must be used only in connection with the Next() method.

## Description
Avoid getting the dataset when an enumeration is not used, which will decrease performance.

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Reason for the rule
If you use `FindSet()` or `Find()` you must have a `Next()` method. Otherwise, you are wasting CPU and bandwidth since multiple records are loaded but you only use one.

## Bad code example
```AL
codeunit 1 MyCodeunit
{
   var
      customer: Record Customer;
                
   procedure Foo()
   begin
      if customer.FindFirst() then
         repeat
         ...
         until customer.Next() = 0;
      end;
}
```

## Good code example
```AL
codeunit 1 MyCodeunit
{
   var
      customer : Record Customer;
                
   procedure Foo()
   begin
      if customer.FindSet() then
         repeat
         ...
         until customer.Next() = 0;
      end;
}
```

## See Also  
[CodeCop Analyzer](codecop.md)  
[Get Started with AL](../devenv-get-started.md)  
[Developing Extensions](../devenv-dev-overview.md)  