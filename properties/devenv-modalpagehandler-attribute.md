---
title: "ModalPageHandler Attribute"
description: "The ModalPageHandler attribute in AL for Business Central"
ms.date: 04/01/2021
ms.topic: reference
author: jswymer
---

# ModalPageHandler Attribute

Specifies that the method is a ModalPageHandler method.

## Applies to  
AL test methods on test codeunits. A test method is a method that has the [Test Attribute](devenv-test-attribute.md) declared. 

## Syntax  
  
```AL
[ModalPageHandler]
procedure ModalPageHandler(var Page: TestPage)
```    
  
## Remarks

The **ModalPageHandler** method is called when a modal page is invoked in the code.

The **ModalPageHandler** attribute requires that the method where it is applied has the signature `ModalPageHandler(var Page: TestPage)`. The parameter variable, *TestPage*, is the specific page in this case.

## See Also

[AL Method Reference](../methods-auto/library.md)  
[Method Attributes](devenv-method-attributes.md)  
[Test Codeunits and Test Functions](../devenv-test-codeunits-and-test-methods.md)