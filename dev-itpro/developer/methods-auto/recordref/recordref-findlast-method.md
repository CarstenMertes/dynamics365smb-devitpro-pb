---
title: "RecordRef.FindLast() Method"
description: "Finds the last record in a table based on the current key and filter."
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
# RecordRef.FindLast() Method
> **Version**: _Available or changed with runtime version 1.0._

Finds the last record in a table based on the current key and filter.


## Syntax
```AL
[Ok := ]  RecordRef.FindLast()
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
 You should use this method instead of Find\('+'\) when you need only the last record.  
  
 You should use this method only when you explicitly want to find the last record in a table or set. Do not use this method in combination with repeat..until.  
  
## Example  
 The following example opens the Item table \(27\) as a RecordRef variable that is named ItemRecref. The FindLast method searches for the last record in the table. If the record is found, the description and unit price of the item in the record are displayed in a message box. Otherwise, a message that indicates that the last item was not found is displayed.
 
```al
var
    ItemRecref: RecordRef;
    Text000: Label 'The last item is %1 and the unit price is %2.';
    Text001: Label 'The last item was not found.';
begin    
    ItemRecref.Open(27);  
    if ItemRecref.FindLast then  
      Message(Text000, ItemRecref.Field(3),  ItemRecref.Field(18))  
    else  
      Message(Text001);  
end;
  
```  

## See Also
[RecordRef Data Type](recordref-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)