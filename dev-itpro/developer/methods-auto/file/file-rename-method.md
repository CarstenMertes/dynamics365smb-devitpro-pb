---
title: "File.Rename(Text, Text) Method"
description: "Renames an ASCII or binary file."
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
# File.Rename(Text, Text) Method
> **Version**: _Available or changed with runtime version 1.0._

Renames an ASCII or binary file.

> [!NOTE]
> This method is supported only in Business Central on-premises.

## Syntax
```AL
[Ok := ]  File.Rename(OldName: Text, NewName: Text)
```
> [!NOTE]
> This method can be invoked without specifying the data type name.
## Parameters
*OldName*  
&emsp;Type: [Text](../text/text-data-type.md)  
The current name of the file that you want to change, including its path. When you enter the path, consider these shortcuts:
-   You can omit the drive designation, if the file is located on the current drive.
-   You can omit the full path, if the file is located in the current directory.
-   You can enter only the subdirectory name, if the file is located in a subdirectory of the current directory.  

*NewName*  
&emsp;Type: [Text](../text/text-data-type.md)  
The new name that you want to assign to the file, including its path. When you enter the path, consider these shortcuts:
-   You can omit the drive designation, if the file is located on the current drive.
-   You can omit the full path, if the file is located in the current directory.
-   You can enter only the subdirectory name, if the file is located in a subdirectory of the current directory.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the operation was successful; otherwise **false**.   If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

Typically, the return value is **false** if the file does not exist, or if the file is a system or hidden file.  
  
## Example  

The following example changes the name of a text file that is named Testfile.txt to NewTestFile.txt. The path of the file that is renamed is C:\\TestFolder\\Testfile.txt. The name and path are stored in the varOldFile variable. The new name and path of the file are stored the varNewfile variable. The RENAME method uses the variables to change the name of the file. This example assumes that you have created the following file on your computer: C:\\TestFolder\\Testfile.txt. 

```al
 var
    varOldfile: Text;
    varNewfile: Text;
begin
    varOldfile := 'C:\TestFolder\Testfile.txt' ;  
    varNewfile := 'C:\TestFolder\NewTestFile.txt';  
    Rename(varOldfile, varNewfile);  
end;
```  
  
## See Also

[File Data Type](file-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)