---
title: "RecordRef.Duplicate() Method"
description: "Duplicates the table that contains the RecordRef."
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
# RecordRef.Duplicate() Method
> **Version**: _Available or changed with runtime version 1.0._

Duplicates the table that contains the RecordRef.


## Syntax
```AL
RecordRef :=   RecordRef.Duplicate()
```

## Parameters
*RecordRef*  
&emsp;Type: [RecordRef](recordref-data-type.md)  
An instance of the [RecordRef](recordref-data-type.md) data type.  

## Return Value
*RecordRef*  
&emsp;Type: [RecordRef](recordref-data-type.md)  
A RecordRef that refers to a new record with the same filters, current keys, and marks as the original RecordRef.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  
 The RecordRef that is returned refers to a new record with the same filters, current keys, and marks as the original RecordRef. Any changes that you make to the filters, current keys, and marks of the new record are not observed in the original. This differs from assigning one RecordRef to another RecordRef. If you assign one RecordRef to another RecordRef, then both refer to the same record and changes that you make to one RecordRef are observed in the other RecordRef.  
  
## Example  
 The following example opens table 18 \(Customer\) as a RecordRef variable named RecordRef1 and uses the DUPLICATE method to copy the filters, current keys and marks from RecordRef1 into a new RecordRef variable named RecordRef2. After the DUPLICATE method is executed, the RecordRef1 and RecordRef2 variables are identical. 
 
```al
var
    RecordRef1: RecordRef;
    RecordRef2: RecordRef;
    Text000: Label 'RecordRef1 refers to the %1 table.\\ RecordRef2 refers to the %2 table.';
begin   
    RecordRef1.Open(18);  
    RecordRef2 := RecordRef1.Duplicate;  
    Message(Text000, RecordRef1.Caption, RecordRef2.Caption); 
end; 
```  

## See Also
[RecordRef Data Type](recordref-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)