---
title: "File.CreateTempFile([TextEncoding]) Method"
description: "Creates a temporary file."
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
# File.CreateTempFile([TextEncoding]) Method
> **Version**: _Available or changed with runtime version 1.0._

Creates a temporary file. This enables you to save data of any format to a temporary file. This file has a unique name and will be stored in a temporary file folder.

> [!NOTE]
> This method is supported only in Business Central on-premises.

## Syntax
```AL
[Ok := ]  File.CreateTempFile([Encoding: TextEncoding])
```
> [!NOTE]
> This method can be invoked without specifying the data type name.
## Parameters
*File*  
&emsp;Type: [File](file-data-type.md)  
An instance of the [File](file-data-type.md) data type.  

*[Optional] Encoding*  
&emsp;Type: [TextEncoding](../textencoding/textencoding-option.md)  
The encoding that will be used by the stream. The default encoding is MSDos.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

You can use this method together with [Name Method \(File\)](../../methods-auto/file/file-name-method.md) and [Close Method \(File\)](../../methods-auto/file/file-close-method.md).  
  
## Example  

This example creates a temporary file that has the text Hello and then deletes the file by using the File.Close method.

```al
 var
    FileName: File;
begin
    FileName.CreateTempFile;  
    FileName.Write('Hello');  
    FileName.Close; 
end;
```  
  
## See Also
[File Data Type](file-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)