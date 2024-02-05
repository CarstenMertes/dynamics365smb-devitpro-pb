---
title: "Version.Create(Integer, Integer [, Integer] [, Integer]) Method"
description: "Creates a version object from the major, minor, build and revision numbers provided."
ms.author: solsen
ms.custom: na
ms.date: 03/02/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Version.Create(Integer, Integer [, Integer] [, Integer]) Method
> **Version**: _Available or changed with runtime version 1.0._

Creates a version object from the major, minor, build and revision numbers provided.


## Syntax
```AL
Value :=   Version.Create(Major: Integer, Minor: Integer [, Build: Integer] [, Revision: Integer])
```
## Parameters
*Major*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The major version number.  

*Minor*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The minor version number.  

*[Optional] Build*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The build version number.  

*[Optional] Revision*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The revision version number.  


## Return Value
*Value*  
&emsp;Type: [Version](version-data-type.md)  
The version created from the provided major, minor, build and revision numbers.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[Version Data Type](version-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)