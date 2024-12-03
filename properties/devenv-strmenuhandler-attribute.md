---
title: "StrMenuHandler Attribute"
description: "The StrMenuHandler attribute in AL for Business Central"
ms.date: 04/01/2021
ms.topic: reference
author: jswymer
---

# StrMenuHandler Attribute

Specifies that the method is a StrMenuHandler method.

## Applies to  
AL methods on test codeunits. A test codeunit is a codeunit that has the [SubType Property](../properties/devenv-subtype-property.md) set to **Test**. 

## Syntax  
  
```AL
[StrMenuHandler]
procedure StrMenuHandler(Option: Text[1024]; var Choice: Integer; Instruction: Text[1024])
```    

## Remarks

The **StrMenuHandler** method is called when a StrMenu method is invoked in code.

The **StrMenuHandler** attribute requires that the method where it is applied has the signature `procedure StrMenuHandler(Option: Text[1024]; var Choice: Integer; Instruction: Text[1024])`.The parameter type, *Text*,  contains the text of the method and *Choice* is the option chosen in the StrMenu. *Options* is the list of the different option values and *Instruction* is the leading text.

## See Also

[AL Method Reference](../methods-auto/library.md)  
[Method Attributes](devenv-method-attributes.md)  
[Test Codeunits and Test Functions](../devenv-test-codeunits-and-test-methods.md)  
