---
title: "System.ImportObjects(Text [, Integer]) Method"
description: "Imports application objects from a file."
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
# System.ImportObjects(Text [, Integer]) Method
> **Version**: _Available or changed with runtime version 1.0 until version 1.0 where it was deprecated._

Imports application objects from a file.

> [!NOTE]
> This method is supported only in Business Central on-premises.

## Syntax
```AL
 System.ImportObjects(FileName: Text [, Format: Integer])
```
> [!NOTE]
> This method can be invoked without specifying the data type name.
## Parameters
*FileName*  
&emsp;Type: [Text](../text/text-data-type.md)  
The path of the file from which the objects will be imported.  

*[Optional] Format*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The format in which the objects are represented in the file.  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[System Data Type](system-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)