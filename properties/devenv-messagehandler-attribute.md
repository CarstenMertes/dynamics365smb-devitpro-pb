---
title: "MessageHandler Attribute"
description: "The MessageHandler attribute in AL for Business Central"
ms.date: 04/01/2021
ms.topic: reference
author: jswymer
---

# MessageHandler Attribute

Specifies that the method is a MessageHandler method.

## Applies to  
AL test methods on test codeunits. A test method is a method that has the [Test Attribute](devenv-test-attribute.md) declared. 

## Syntax  
  
```AL
[MessageHandler]
procedure MessageHandler(Message : Text[1024])
```    

## Remarks

The **MessageHandler** method is called when a message method is invoked in the code. 

The **MessageHandler** attribute requires that the method where it is applied has the signature `MessageHandler(Message: Text[1024])`. The parameter type, *Text*,  contains the text of the method.

## See Also

[AL Method Reference](../methods-auto/library.md)  
[Method Attributes](devenv-method-attributes.md)  
[Test Codeunits and Test Functions](../devenv-test-codeunits-and-test-methods.md)