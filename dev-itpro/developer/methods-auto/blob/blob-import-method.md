---
title: "Blob.Import(Text) Method"
description: "Imports a binary large object (BLOB) from a file."
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
# Blob.Import(Text) Method
> **Version**: _Available or changed with runtime version 1.0._

Imports a binary large object (BLOB) from a file.

> [!NOTE]
> From runtime version 9.0 and onward, this method is only supported in Business Central on-premises.

## Syntax
```AL
[ImportName := ]  Blob.Import(Name: Text)
```
## Parameters
*Blob*  
&emsp;Type: [Blob](blob-data-type.md)  
An instance of the [Blob](blob-data-type.md) data type.  

*Name*  
&emsp;Type: [Text](../text/text-data-type.md)  
The path and name of the BLOB that you want to import. When you enter the path, consider the following shortcuts:
-   You can omit the drive letter if the command is located on the current drive.
-   You can omit the full path if the command is located in the current directory.
-   You can enter only the subdirectory name if the command is located in a subdirectory of the current directory.  


## Return Value
*[Optional] ImportName*  
&emsp;Type: [Text](../text/text-data-type.md)  
The name of the imported file.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[Blob Data Type](blob-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)