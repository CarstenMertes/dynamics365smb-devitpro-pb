---
title: "RecordRef.FieldIndex(Integer) Method"
description: "Gets the FieldRef of the field that has the specified index in the table that is referred to by the RecordRef."
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
# RecordRef.FieldIndex(Integer) Method
> **Version**: _Available or changed with runtime version 1.0._

Gets the FieldRef of the field that has the specified index in the table that is referred to by the RecordRef.


## Syntax
```AL
Field :=   RecordRef.FieldIndex(Index: Integer)
```
## Parameters
*RecordRef*  
&emsp;Type: [RecordRef](recordref-data-type.md)  
An instance of the [RecordRef](recordref-data-type.md) data type.  

*Index*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The index of the field.  


## Return Value
*Field*  
&emsp;Type: [FieldRef](../fieldref/fieldref-data-type.md)  
The FieldRef of the field that has the specified index.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  
 The fields in the primary key are always listed first in the index. Therefore, the order of the fields in the index is not necessarily the same as the order of the fields in the table.  

 If the index is out of the range supplied or if no table is selected, then the method returns an error.  

## Example  

```al
var
    SalesInvHdr: RecordRef;
    FldRef: FieldRef;
    Str: Text[1024];
    Text001: Label 'Index 1: %1\\';
    Text002: Label 'Index 2: %2\\';
    Text003: Label 'Index 3: %3';
begin
    SalesInvHdr.Open(112);  
    FldRef1 := SalesInvHdr.FieldIndex(1);  
    FldRef2 := SalesInvHdr.FieldIndex(2);  
    FldRef3 := SalesInvHdr.FieldIndex(3);  
    Message(Text001 + Text002 + Text003, FldRef1.Caption, FldRef2.Caption, FldRef3.Caption);  
end;
```  

 The message window displays the following:  

-   **Index 1: No.**  

-   **Index 2: Sell-to Customer No.**  

-   **Index 3: Bill-to Customer No.**  

 The following illustration shows the first fields in table 112, Sales Invoice Header, and shows the keys for table 112. The order of the fields in the index differs from the order of the fields in the table. The index lists the field in the primary key first.  


## See Also
[RecordRef Data Type](recordref-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)