---
title: "RecordRef.KeyIndex(Integer) Method"
description: "Gets the KeyRef of the key that has the index specified in the table that is currently selected."
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
# RecordRef.KeyIndex(Integer) Method
> **Version**: _Available or changed with runtime version 1.0._

Gets the KeyRef of the key that has the index specified in the table that is currently selected. The key can be composed of fields of any supported data type. Data types that are not supported include BLOBs, FlowFilters, variables, and functions. If the sorting key is set to a field that is not part of a key, then the KEYINDEX is -1.


## Syntax
```AL
Key :=   RecordRef.KeyIndex(Index: Integer)
```
## Parameters
*RecordRef*  
&emsp;Type: [RecordRef](recordref-data-type.md)  
An instance of the [RecordRef](recordref-data-type.md) data type.  

*Index*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The number of the index in which you are interested.  


## Return Value
*Key*  
&emsp;Type: [KeyRef](../keyref/keyref-data-type.md)  
The KeyRef of the field that has the specified index.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  
 The first key in the index must have index 1, the second index 2, and so on. The last key must have index = KeyCount. If the specified index is out of the range or if no table is selected, the method returns an error.  
  
## Example  
 The following example opens table 18 \(Customer\) as a RecordRef variable that is named CustomerRecref. The loop starts from 1 and loops through the key indexes that are in the table. `CustomerRecref.KeyCount` returns the maximum number of keys that are defined in the table. The loop continues until the last key is reached. For each index that is specified, the KeyIndex method retrieves the KeyRef for the specified index. The key index and the KeyRef for the specified indexes are displayed in a message box. 
  
```al
var
    CustomerRecref: RecordRef;
    i: Integer;
    varKeyRef: KeyRef;
    Text000: Label 'KeyIndex: %1   KeyRef: %2'; 
begin
    CustomerRecref.Open(18);  
      for i := 1 to CustomerRecref.KeyCount do begin  
        varKeyRef := CustomerRecref.KeyIndex(i);  
        Message(Text000, i, varKeyRef);  
      end;  
    CustomerRecref.Close;  
end;
```  
  

## See Also
[RecordRef Data Type](recordref-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)