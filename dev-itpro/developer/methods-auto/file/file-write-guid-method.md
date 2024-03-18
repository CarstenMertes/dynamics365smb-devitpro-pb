---
title: "File.Write(Guid) Method"
description: "Writes to an MS-DOS encoded file or binary file."
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
# File.Write(Guid) Method
> **Version**: _Available or changed with runtime version 1.0._

Writes to an MS-DOS encoded file or binary file.

> [!NOTE]
> This method is supported only in Business Central on-premises.

## Syntax
```AL
 File.Write(Value: Guid)
```
> [!NOTE]
> This method can be invoked without specifying the data type name.
## Parameters
*File*  
&emsp;Type: [File](file-data-type.md)  
An instance of the [File](file-data-type.md) data type.  

*Value*  
&emsp;Type: [Guid](../guid/guid-data-type.md)  
The data that you want to write to the file.  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  
 You must call the [TextMode Method \(File\)](../../methods-auto/file/file-textmode-method.md) before you call the Write method.  
  
 If [TextMode Method \(File\)](../../methods-auto/file/file-textmode-method.md) is set to **true** and *Value* is an integer, then the integer is written as text, followed by a new line character.  
  
 If *Value* is a record, each field is separated by a tab character.  
  
 If [TextMode Method \(File\)](../../methods-auto/file/file-textmode-method.md) is **false** and *Value* is an integer, an integer is written that is four bytes long.  
  
 MS-DOS encoding requires a different character set for each language. MS-DOS text is encoded to the internal Unicode data type by using the system locale language of the computer that is running [!INCLUDE[d365fin_server_md](../../includes/d365fin_server_md.md)]. If you write to a file that uses MS-DOS encoding, then you must set the system locale language of the computer that is running [!INCLUDE[d365fin_server_md](../../includes/d365fin_server_md.md)] to match the language of the data that you want to write to the file.  
  
 We recommend that you use the File data type for files that were created in earlier versions of [!INCLUDE[d365fin_md](../../includes/d365fin_md.md)].  
  
 To read or write files in Unicode or in other formats, we recommend that you use .NET Framework interoperability and use the [System.IO Namespace](/dotnet/api/system.io).  
  
## Example  
 The following example determines whether the specified file exists. If it exists, the [WriteMode Method \(File\)](file-writemode-method.md) allows the file to be open for writing. The [Open Method \(File\)](file-open-method.md) opens the file, the [Write Method \(File\)](file-writemode-method.md) writes the text “Hello World” to the file and then the [Close Method \(File\)](file-close-method.md) closes the file. If the file does not exist, then an error message is displayed. This example assumes that you have created the following file: C:\\TestFolder\\TestFile.txt. 
 
```al
var
    FileName: Text;
    TestFile: File;
    Guid1: GUID;
begin
    FileName := 'C:\TestFolder\TestFile.txt';  
    if Exists(FileName) then begin
      TestFile.WriteMode(True);  
      TestFile.Open(FileName);  
      TestFile.Write(Guid1);  
      TestFile.Close;  
    end else 
      Message('%1 does not exit.', FileName);
end;
```
  
## See Also
[File Data Type](file-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)