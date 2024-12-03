---
title: "TryMethod Property"
ms.date: 05/12/2020
ms.topic: article
author: SusanneWindfeldPedersen
---

# TryMethod Property
Specifies the method to be try method, which can be used to catch and handle errors and exceptions that occur when code is run.  
  
## Applies to  
- AL methods 
  
> [!NOTE]  
> In test and upgrade codeunits, this property only applies to normal methods as specified by the [Normal Attribute \(Test Codeunits\)](../methods/devenv-normal-attribute.md) or [MethodType Property \(Upgrade Codeunits\)](devenv-methodtype-property-upgrade-codeunits.md).  
  
## Remarks  

Try methods in AL enable you to handle errors that occur in the application during code execution. For example, with try methods, you can provide more user-friendly error messages to the end user than those thrown by the system. You can use try methods to catch errors/exceptions that thrown by [!INCLUDE[prodshort](includes/prodshort.md)] or exceptions that are thrown during .NET Framework interoperability operations.  

For more information, see [Handling Errors by Using Try Methods](../devenv-handling-errors-using-try-methods.md).  

## See Also  

[Essential AL Methods](../devenv-essential-al-methods.md)  
[Handling Errors by Using Try Methods](../devenv-handling-errors-using-try-methods.md)  
[Properties](devenv-properties.md)