---
title: "SessionSettingsHandler Attribute"
description: "The SessionSettingsHandler attribute in AL for Business Central"
ms.date: 04/01/2021
ms.topic: reference
author: jswymer
---

# SessionSettingsHandler Attribute

Specifies that the method is a SessionSettingsHandler method.

## Applies to  
AL methods on test codeunits. A test codeunit is a codeunit that has the [SubType Property](../properties/devenv-subtype-property.md) set to **Test**. 

## Syntax  
  
```AL
[SessionSettingsHandler]
procedure SessionSettingsHandler(var SessionSettings: SessionSettings) : Boolean
```    

## Remarks

The **SessionSettingsHandler** method is called when SessionSetting is updated. 

The **SessionSettingsHandler** attribute requires that the method where it is applied has the signature `SessionSettingsHandler(var SessionSettings: SessionSettings) : Boolean`. The parameter variable, *SessionSettings*, holds the new settings.

## See Also

[AL Method Reference](../methods-auto/library.md)  
[Method Attributes](devenv-method-attributes.md)  
[Test Codeunits and Test Functions](../devenv-test-codeunits-and-test-methods.md)