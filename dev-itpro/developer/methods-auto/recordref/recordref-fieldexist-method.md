---
title: "RecordRef.FieldExist(Integer) Method"
description: "Determines if the field that has the number FieldNo exists in the table that is referred to by the RecordRef."
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
# RecordRef.FieldExist(Integer) Method
> **Version**: _Available or changed with runtime version 1.0._

Determines if the field that has the number FieldNo exists in the table that is referred to by the RecordRef. Returns an error if no table is currently selected.


## Syntax
```AL
Exist :=   RecordRef.FieldExist(FieldNo: Integer)
```
## Parameters
*RecordRef*  
&emsp;Type: [RecordRef](recordref-data-type.md)  
An instance of the [RecordRef](recordref-data-type.md) data type.  

*FieldNo*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The FieldNo that you want to know whether exists in the table.  


## Return Value
*Exist*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the field exists; otherwise **false**.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Example  
 The following example opens table 18 \(Customer\) as a RecordRef variable that is named MyRecordRef. The code loops through fields 1 through 12 and uses the FieldEXIST method to determine whether the specified field exists. If the field exists, the name of the field and a message that indicates that the field exists is displayed. Otherwise, a message that indicates that the field does not exist is displayed. 
  
```al
var
    MyRecordRef: RecordRef;
    i: Integer;
    VarFieldName: FieldRef;
    Text000: Label 'The %1 table contains %2 field\(s\).\\';
begin  
    MyRecordRef.Open(18);  
    for i := 1 to 12 do begin  
      if MyRecordRef.FieldExist(i) then begin  
         VarFieldName := MyRecordRef.Field(i);  
         Message(Text000, i, VarFieldName.Name);  
        end else  
        Message(Text001, i);  
      end;  
end;
```  
  

## See Also
[RecordRef Data Type](recordref-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)