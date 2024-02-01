---
title: "OutStream.Write(Option [, Integer]) Method"
description: "Writes a specified number of bytes to the stream."
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
# OutStream.Write(Option [, Integer]) Method
> **Version**: _Available or changed with runtime version 1.0._

Writes a specified number of bytes to the stream. Data is written in binary format.


## Syntax
```AL
[Written := ]  OutStream.Write(Value: Option [, Length: Integer])
```
## Parameters
*OutStream*  
&emsp;Type: [OutStream](outstream-data-type.md)  
An instance of the [OutStream](outstream-data-type.md) data type.  

*Value*  
&emsp;Type: [Option](../option/option-data-type.md)  
Contains the data to be written.  

*[Optional] Length*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The number of bytes to be written. In the case of data types other than string, code, and binary, if you specify a length that differs from the size of the variable, an error message is displayed.  


## Return Value
*[Optional] Written*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The number of bytes that were written. If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  
 If the optional return value, *Written*, is not specified and it was not possible to write all the data, an error message is displayed.  
  
 If the return value is present, you must verify that all the data was streamed.  
  
## Example  
  
```al
 var
    recBinaries: Record "Company Information";
    OStream: OutStream;
    Opt: Option;
begin
    recBinaries.Find('-');  
    recBinaries.Picture.CreateOutstream(OStream);   
    OStream.Write(Opt);  
    recBinaries.Modify(); 
end;
```   
  

## See Also
[OutStream Data Type](outstream-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)