---
title: "KeyRef.FieldCount() Method"
description: "Gets the number of fields that have been defined in a key."
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
# KeyRef.FieldCount() Method
> **Version**: _Available or changed with runtime version 1.0._

Gets the number of fields that have been defined in a key. Returns an error if no key is selected.


## Syntax
```AL
No :=   KeyRef.FieldCount()
```
> [!NOTE]
> This method can be invoked using property access syntax.

## Parameters
*KeyRef*  
&emsp;Type: [KeyRef](keyref-data-type.md)  
An instance of the [KeyRef](keyref-data-type.md) data type.  

## Return Value
*No*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The number of fields that have been defined in the key.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Example

The following example retrieves the number of fields that are defined in a key in record. The table with ID 18 \(the Customer table\) is open with a reference to table 18. The [KeyIndex Method \(RecordRef\)](../library.md) method retrieves the second key in the record and store the *KeyRef* in the varKeyRef variable. The [FieldCount Method \(KeyREF\)](../library.md) is then used to return the number of fields defined in the key and displayed in a message box.
 
```al
var
    RecRef: RecordRef;
    varKeyRef: KeyRef;
    VarCount: Integer;
begin 
    RecRef.Open(18);  
    varKeyRef := RecRef.KeyIndex(2);  
    VarCount := varKeyRef.FieldCount;  
    Message('The number of fields defined in the key is: %1', VarCount);  
end;
```  
  

## See Also
[KeyRef Data Type](keyref-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)