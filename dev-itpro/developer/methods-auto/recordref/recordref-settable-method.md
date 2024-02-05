---
title: "RecordRef.SetTable(Record) Method"
description: "Sets the table to which a Record variable refers as the same table as a RecordRef variable."
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
# RecordRef.SetTable(Record) Method
> **Version**: _Available or changed with runtime version 1.0._

Sets the table to which a Record variable refers as the same table as a RecordRef variable.


## Syntax
```AL
 RecordRef.SetTable(Rec: Record)
```
## Parameters
*RecordRef*  
&emsp;Type: [RecordRef](recordref-data-type.md)  
An instance of the [RecordRef](recordref-data-type.md) data type.  

*Rec*  
&emsp;Type: [Record](../record/record-data-type.md)  
Specifies the Record that you want to refer to the table.  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  
 Any filters that are applied to the RecordRef are also applied to the Record. If you change the filter that is applied to the RecordRef, you must call SetTable again to apply the new filter to the Record.  

## Example  
 This example shows that if you have a RecordID data type, you can get a RecordRef for the table that the RecordID refers to. Then you can use the RecordRef to set the table to which a Record variable refers.  

```al
var
    RecRef: RecordRef;
    InvtEventBuf: Record "Inventory Event Buffer";
    RecID: RecordId;
    ProdOrderComp: Record "Prod. Order Component";
begin 
    InvtEventBuf.Find('-');  
    RecID := InvtEventBuf."Source Line ID";  
    RecRef := RecID.GetRecord;  
    RecRef.SetTable(ProdOrderComp);  
end;
```  


## See Also
[RecordRef Data Type](recordref-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)