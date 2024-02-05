---
title: "Blob.Export(Text) Method"
description: "Exports a binary large object (BLOB) to a file."
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
# Blob.Export(Text) Method
> **Version**: _Available or changed with runtime version 1.0._

Exports a binary large object (BLOB) to a file.

> [!NOTE]
> From runtime version 9.0 and onward, this method is only supported in Business Central on-premises.

## Syntax
```AL
[ExportName := ]  Blob.Export(Name: Text)
```
## Parameters
*Blob*  
&emsp;Type: [Blob](blob-data-type.md)  
An instance of the [Blob](blob-data-type.md) data type.  

*Name*  
&emsp;Type: [Text](../text/text-data-type.md)  
The path and name of the BLOB that you want to export. When you enter the path, consider these shortcuts:
-   You can omit the drive letter if the command is located on the current drive.
-   You can omit the full path if the command is located in the current directory.
-   You can enter only the subdirectory name if the command is located in a subdirectory of the current directory.  


## Return Value
*[Optional] ExportName*  
&emsp;Type: [Text](../text/text-data-type.md)  
The name of the created file.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[Blob Data Type](blob-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)