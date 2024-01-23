---
title: "RecordRef.SystemIdNo() Method"
description: "Gets the field number that is used by the SystemId field."
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
# RecordRef.SystemIdNo() Method
> **Version**: _Available or changed with runtime version 4.0._

Gets the field number that is used by the SystemId field. The SystemId field is a system field that the platform adds to all table objects.


## Syntax
```AL
SystemIdFieldNo :=   RecordRef.SystemIdNo()
```
> [!NOTE]
> This method can be invoked using property access syntax.

## Parameters
*RecordRef*  
&emsp;Type: [RecordRef](recordref-data-type.md)  
An instance of the [RecordRef](recordref-data-type.md) data type.  

## Return Value
*SystemIdFieldNo*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The field number of the SystemId field.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Example
  
This example shows how to use the SystemIdNo method to retrieve the field number that is used by the SystemId field of a table.

```al
var
    CustomerRec: Record Customer;
    SystemIdFieldNo: Integer;
    Text000: Label 'The field number is: %1.';

begin
    CustomerRec.Open(Database::Customer);
    SystemIdFieldNo := CustomerRec.SystemIdNo();
    Message(Text000, Format(SystemIdFieldNo));
end;
```

## See Also

[SystemId Field](../../devenv-table-system-fields.md#systemid)  
[RecordRef Data Type](recordref-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)
