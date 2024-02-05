---
title: "System.GetLastErrorCode() Method"
description: "Gets the classification of the last error that occurred."
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
# System.GetLastErrorCode() Method
> **Version**: _Available or changed with runtime version 1.0._

Gets the classification of the last error that occurred.


## Syntax
```AL
String :=   System.GetLastErrorCode()
```
> [!NOTE]
> This method can be invoked using property access syntax.
> [!NOTE]
> This method can be invoked without specifying the data type name.

## Return Value
*String*  
&emsp;Type: [Text](../text/text-data-type.md)  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

You use the GetLastErrorCode method to identify the type of the last error that occurred. You use the [GetLastErrorText Method](../../methods-auto/system/system-getlasterrortext--method.md) to get the details of the last error.  
  
The result of the GetLastErrorCode method is not translated into the local language. The result of the [GetLastErrorText Method](../../methods-auto/system/system-getlasterrortext--method.md) is translated into the local language.  
  
## Example

This example opens a file and then causes an error to occur by trying to open the file again. If the code for the error that occurred is not the expected error code, then an error message is displayed.  

```al
var
    ErrorCode: Text[1024];  
    ExpectedErrorCode: Text[1024];  
    FileObj1: File;
    FileObj2: File;
    Text0001: Label 'The error code is not valid. Expected: %1. Actual: %2. Error message: %3';
begin
    ExpectedErrorCode := 'StreamIO';  
    FileObj1.CreateTempFile;  
    AssertError FileObj2.Create(FileObj1.Name);  
    ErrorCode := GetLastErrorCode;  
    if ErrorCode <> ExpectedErrorCode then  
      Error(Text001, ExpectedErrorCode, ErrorCode, GetLastErrorText);  
end;
``` 
 
## See Also

[System Data Type](system-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)