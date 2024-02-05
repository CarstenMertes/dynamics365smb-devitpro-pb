---
title: "System.IsNull(DotNet) Method"
description: "Gets a value indicating whether a DotNet object has been created or not."
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
# System.IsNull(DotNet) Method
> **Version**: _Available or changed with runtime version 2.0._

Gets a value indicating whether a DotNet object has been created or not.

> [!NOTE]
> This method is supported only in Business Central on-premises.

## Syntax
```AL
Ok :=   System.IsNull(DotNet: DotNet)
```
> [!NOTE]
> This method can be invoked without specifying the data type name.
## Parameters
*DotNet*  
&emsp;Type: [DotNet](../dotnet/dotnet-data-type.md)  
A DotNet expression.  


## Return Value
*Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**True** if the DotNet object is NULL, otherwise **false**.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[System Data Type](system-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)