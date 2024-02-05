---
title: "RecordRef.Insert() Method"
description: "Inserts a record into a table without executing the code in the OnInsert trigger."
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
# RecordRef.Insert() Method
> **Version**: _Available or changed with runtime version 1.0._

Inserts a record into a table without executing the code in the OnInsert trigger.


## Syntax
```AL
[Ok := ]  RecordRef.Insert()
```

## Parameters
*RecordRef*  
&emsp;Type: [RecordRef](recordref-data-type.md)  
An instance of the [RecordRef](recordref-data-type.md) data type.  

## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the operation was successful; otherwise **false**.   If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  
 Records are uniquely identified by the values in primary key fields. The Database Management System \(DBMS\) checks the primary key for the table before it inserts a new record.  
  
 If the table contains an auto-increment field, the auto-increment feature is used if the record contains a zero value in that field. The auto-increment feature enters the new value into the field as part of the insert.  
  
 If the auto-increment field contains a non-zero value, that value is inserted into the table and the auto-increment feature is not used. If the value in the auto-increment field is greater than the last auto-increment value in the table, the next auto-increment value that is entered into the table will be greater than the value in the field that you just inserted. If the value in the auto-increment field already exists in the table, a run-time error occurs.  
  
 This method works the same as the [Insert Method \(Record\)](../record/record-insert--method.md).  
  
## Example  
 The following example opens a table 18 \(Customer\) with a RecordRef variable that is named CustomerRecref. The [Field Method \(RecordRef\)](recordref-field-method.md) creates a FieldRef variable that is named MyFieldRef for the field. The [Init Method \(RecordRef\)](recordref-init-method.md) initializes the values in the fields by using default values and then the Insert method inserts a new record. The new record is 1120. This is the primary key for the new record.  
  
> [!NOTE]  
>  In this example, the Init method is called before the primary key is assigned a value. The Init method does not initialize primary key fields. Therefore calling the [Init Method \(RecordRef\)](recordref-init-method.md) before or after you assign values to the primary key field does not make any difference.  
   
```al
var
    CustomerRecref: RecordRef;
    MyFieldRef: FieldRef;
    Text000: Label 'The value of the field after you insert the record is %1.';
begin 
    CustomerRecref.Open(18);  
    MyFieldRef := CustomerRecref.Field(1);  
    CustomerRecref.Init();  
    MyFieldRef.Value := '1120';  
    CustomerRecref.Insert();  
    Message(‘%1’, MyFieldRef.Value);  
end;
```  

## See Also
[RecordRef Data Type](recordref-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)