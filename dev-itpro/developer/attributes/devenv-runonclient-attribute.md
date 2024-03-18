---
title: "RunOnClient Attribute"
description: "Sets whether a .NET object that is defined by a variable is run on the Business Central Web client or Dynamics 365 Business Central service."
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

# RunOnClient Attribute
> **Version**: _Available or changed with runtime version 1.0._

Sets whether a .NET object that is defined by a variable is run on the Business Central Web client or Dynamics 365 Business Central service.

> [!NOTE]
> This attribute is supported only in Business Central on-premises.

## Applies To

- Variable


## Syntax

```AL
[RunOnClient]
```

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

The **RunOnClient** applies to variables of the **DotNet** data type.  

The **RunOnClient** property is used alongside safe listed APIs that provide access to client-side device capabilities, such as camera or location.

The **RunOnClient** property is part of .NET interoperability in [!INCLUDE[d365fin_long_md](../includes/d365fin_long_md.md)] that you can use to expand your solution using .NET assemblies. With .NET interoperability, you can call methods and properties in a class of a .NET assembly from AL code by defining a variable for the class. When you set the **RunOnClient** property on a variable, then the class instance that is defined by the variable is instantiated on the [!INCLUDE[webclient](../includes/webclient.md)].  

## Example

For an example on how to use the **RunOnClient** attribute, see [Implementing the Camera in AL](../devenv-implement-camera-al.md#example).

## See Also  
[Get Started with AL](../devenv-get-started.md)  
[Developing Extensions](../devenv-dev-overview.md)  