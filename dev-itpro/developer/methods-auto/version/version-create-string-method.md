---
title: "Version.Create(Text) Method"
description: "Creates a version object from the provided string."
ms.author: solsen
ms.custom: na
ms.date: 03/24/2022
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Version.Create(Text) Method
> **Version**: _Available or changed with runtime version 1.0._

Creates a version object from the provided string. The string should be in the format W.X.Y.Z, where W, X, Y and Z represent positive integers and where Y and Z are optional. If the input string is not in the expected format, an exception is thrown.


## Syntax
```AL
Value :=   Version.Create(Version: Text)
```
## Parameters
*Version*  
&emsp;Type: [Text](../text/text-data-type.md)  
The string to convert into a version object.  


## Return Value
*Value*  
&emsp;Type: [Version](version-data-type.md)  
The version created from the provided string.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[Version Data Type](version-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)