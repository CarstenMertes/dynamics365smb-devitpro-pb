---
title: "System.GetDotNetType(Any) Method"
description: "Gets the System.Type that corresponds to the given value."
ms.author: solsen
ms.custom: na
ms.date: 11/05/2021
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# System.GetDotNetType(Any) Method
> **Version**: _Available or changed with runtime version 2.0._

Gets the System.Type that corresponds to the given value.

> [!NOTE]
> This method is supported only in Business Central on-premises.

## Syntax
```AL
Type :=   System.GetDotNetType(Expression: Any)
```
> [!NOTE]
> This method can be invoked without specifying the data type name.
## Parameters
*Expression*  
&emsp;Type: [Any](../any/any-data-type.md)  
The value for which to retrieve the System.Type.  


## Return Value
*Type*  
&emsp;Type: [DotNet](../dotnet/dotnet-data-type.md)  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[System Data Type](system-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)