---
title: "RecordRef.FindSet([Boolean]) Method"
description: "Finds a set of records in a table based on the current key and filter."
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
# RecordRef.FindSet([Boolean]) Method
> **Version**: _Available or changed with runtime version 1.0._

Finds a set of records in a table based on the current key and filter. FINDSET can only retrieve records in ascending order.


## Syntax
```AL
[Ok := ]  RecordRef.FindSet([ForUpdate: Boolean])
```
## Parameters
*RecordRef*  
&emsp;Type: [RecordRef](recordref-data-type.md)  
An instance of the [RecordRef](recordref-data-type.md) data type.  

*[Optional] ForUpdate*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
Set this parameter to false if you do not want to modify any records in the set. Set this parameter to true if you want to modify records in the set. If you set this parameter to true, the LOCKTABLE method (RecordRef) is immediately performed on the table before the records are read.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the operation was successful; otherwise **false**.   If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

You should use this method only when you explicitly want to loop through a recordset. You should only use this method in combination with `repeat..until`.  

The difference between `Find()` and `FindSet` is that `Find` uses paging and the method only requests N rows in the first request, and then if you need more rows, it'll submit a new SQL request. The `FindSet` method will request all rows at once. 

The difference between `FindSet(false)` and `FindSet(true)` is that `FindSet(true)` will do a `LockTable()` before finding rows, which is an advantage if you plan to update all the rows you are finding.
  
This method works the same way as the [FindSet Method (Record)](../record/record-findset-method.md).  

## Example

The following example opens table 18 **Customer** as a RecordRef variable that is named `MyRecordRef`. The [Field Method)](recordref-field-method.md) creates a FieldRef variable that is named `MyFieldRef` with the first field \(No.\). The [SetFilter Method](../fieldref/fieldref-setfilter-method.md) uses the `MyFieldRef` variable to set a filter that selects records from 30000 to 32000. `MyRecordRef.Field(2)` creates a FieldRef for the second field \(Name\). The `FindSet` method finds the set of records based on the key and the filters that have been set. The *ForUpdate* parameter is set to **False**. This makes the records in the set read-only. The record ID and name of each customer in the record set is displayed in a message box until no records are left in the record set. 
  
```al
var
    MyRecordRef: RecordRef;
    MyFieldRef: FieldRef;
    Text000: Label '%1: "%2" is found in the set of records.';
begin    
    MyRecordRef.Open(18);  
    MyFieldRef := MyRecordRef.Field(1);  
    MyFieldRef.SetFilter('30000..32000');  
    MyFieldRef := MyRecordRef.Field(2);  
    if MyRecordRef.FindSet(False) then begin  
      repeat  
        Message(Text000 , MyRecordRef.RecordId, MyFieldRef.Value);  
      until MyRecordRef.Next = 0;  
    end;  
end;
```  


## See Also
[RecordRef Data Type](recordref-data-type.md)  
[Getting Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)