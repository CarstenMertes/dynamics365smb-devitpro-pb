---
title: "SuppressDispose Attribute"
description: "Specifies if a Microsoft .NET Framework object that is defined by a DotNet variable is disposed when it goes out of scope."
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

# SuppressDispose Attribute
> **Version**: _Available or changed with runtime version 1.0._

Specifies if a Microsoft .NET Framework object that is defined by a DotNet variable is disposed when it goes out of scope.

> [!NOTE]
> This attribute is supported only in Business Central on-premises.

## Applies To

- Variable


## Syntax

```AL
[SuppressDispose]
```

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

The **SuppressDispose** attribute applies to local variables of the **DotNet** data type.  

When a local .NET Framework object is disposed, it can't be assigned outside the scope of its local function. If you want to assign the local **DotNet** variable to a global AL or .NET.

## See Also  
[Get Started with AL](../devenv-get-started.md)  
[Developing Extensions](../devenv-dev-overview.md)  