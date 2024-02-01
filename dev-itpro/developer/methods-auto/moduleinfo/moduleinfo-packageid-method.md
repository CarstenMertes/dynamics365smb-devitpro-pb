---
title: "ModuleInfo.PackageId() Method"
description: "Gets the package ID of the specified application."
ms.author: solsen
ms.custom: na
ms.date: 07/07/2021
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# ModuleInfo.PackageId() Method
> **Version**: _Available or changed with runtime version 7.1._

Gets the package ID of the specified application.


## Syntax
```AL
PackageId :=   ModuleInfo.PackageId()
```
> [!NOTE]
> This method can be invoked using property access syntax.

## Parameters
*ModuleInfo*  
&emsp;Type: [ModuleInfo](moduleinfo-data-type.md)  
An instance of the [ModuleInfo](moduleinfo-data-type.md) data type.  

## Return Value
*PackageId*  
&emsp;Type: [Guid](../guid/guid-data-type.md)  
The package ID of the specified application.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[ModuleInfo Data Type](moduleinfo-data-type.md)  
[Get Started with AL](../../../developer/devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)