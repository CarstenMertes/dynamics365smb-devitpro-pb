---
title: "BigText.Read(InStream) Method"
description: "Streams a BigText object that is stored as a BLOB in a table to a BigText variable."
ms.author: solsen
ms.custom: na
ms.date: 07/07/2021
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# BigText.Read(InStream) Method
> **Version**: _Available or changed with runtime version 1.0._

Streams a BigText object that is stored as a BLOB in a table to a BigText variable.


## Syntax
```AL
[Ok := ]  BigText.Read(InStream: InStream)
```
## Parameters
*BigText*  
&emsp;Type: [BigText](bigtext-data-type.md)  
An instance of the [BigText](bigtext-data-type.md) data type.  

*InStream*  
&emsp;Type: [InStream](../instream/instream-data-type.md)  
The InStream object type that you use to stream a BLOB to a BigText variable.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the read transaction was successful, otherwise **false**.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

To delete the content in a BigText variable, use the [Clear Method](../../methods-auto/system/system-clear-joker-method.md).  
  
```al
Clear(BigText)  
```  

## Example

This example shows how to stream a BigText that is stored as a BLOB in a table to a BigText variable.  
  
```al
var
    Bstr: BigText;
    Istream: InStream;
    EmployeeRec: Record Employee;
begin
    EmployeeRec.Find('-');  
    EmployeeRec.CalcFields(Picture);  
    EmployeeRec.Picture.CreateInStream(Istream);  
    Bstr.Read(Istream);  
end;
```  
  
Use the [CalcFields Method \(Record\)](../../methods-auto/record/record-calcfields-method.md) to calculate the BlobField. A BlobField is a binary large object \(maximum size 2 GB\) and must be calculated if you want to use it in AL or display it in the application.  

## See Also

[BigText Data Type](bigtext-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)