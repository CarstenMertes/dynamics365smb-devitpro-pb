---
title: "FieldRef.Relation() Method"
description: "Finds the table relationship of a given field."
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
# FieldRef.Relation() Method
> **Version**: _Available or changed with runtime version 1.0._

Finds the table relationship of a given field.


## Syntax
```AL
TableNumber :=   FieldRef.Relation()
```
> [!NOTE]
> This method can be invoked using property access syntax.

## Parameters
*FieldRef*  
&emsp;Type: [FieldRef](fieldref-data-type.md)  
An instance of the [FieldRef](fieldref-data-type.md) data type.  

## Return Value
*TableNumber*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)


## Remarks

You can use this method for several purposes such as to determine lookups or to check to see if you have permission to read from a table.  
  
This method is similar to the [Relation Method \(Record\)](../../methods-auto/record/record-relation-method.md).  
  
## Example

The following example opens table 37, the Sales Line table, as a RecordRef variable and creates a reference to field 2 \(Sell-to Customer No.\). The [FieldRef Data Type](fieldref-data-type.md) of field 2 is stored in the MyFieldRef variable. The RELATION method retrieves the number of the table that has a relation with the Sell-To-Customer field \(field 2\). The table number is stored the varRelation variable and displayed in the message box. 

```al
var
    MyFieldRef: FieldRef;
    SaleRecref: RecordRef;
    varRelation: Integer;
    Text000: Label 'Field 2 in the Sales Line (37) table has a relation with table %1.';
begin
    SaleRecref.Open(37);  
    MyFieldRef := SaleRecref.Field(2);  
    varRelation := MyFieldRef.Relation;  
    Message(Text000, varRelation);  
end;
```  
  
## See Also
[FieldRef Data Type](fieldref-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)