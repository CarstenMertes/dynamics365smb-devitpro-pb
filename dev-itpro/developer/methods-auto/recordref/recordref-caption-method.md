---
title: "RecordRef.Caption() Method"
description: "Gets the caption of the table that is currently selected."
ms.author: solsen
ms.custom: na
ms.date: 03/24/2022
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# RecordRef.Caption() Method
> **Version**: _Available or changed with runtime version 1.0._

Gets the caption of the table that is currently selected. Returns an error if no table is selected.


## Syntax
```AL
Caption :=   RecordRef.Caption()
```
> [!NOTE]
> This method can be invoked using property access syntax.
## Parameters
*RecordRef*  
&emsp;Type: [RecordRef](recordref-data-type.md)  
An instance of the [RecordRef](recordref-data-type.md) data type.  

## Return Value
*Caption*  
&emsp;Type: [Text](../text/text-data-type.md)  
The caption of the table.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  
 This method works just like the [TableCaption Method (Record)](../record/record-tablecaption-method.md).  
  
## Example  
 The following example selects tables 3 through 5 and opens each table as a RecordRef variable that is named MyRecordRef. The Caption method uses the RecorRef variable to retrieve the caption for each of the tables and displays the table number and the caption in a message box. The [Close Method (RecordRef)](recordref-close-method.md) closes the table.
  
```al
var
    varCaption: Text;
    i: Integer;
    MyRecordRef: RecordRef;
    Text000: Label 'Table No: %1 Caption: %2';
begin
    for i := 3 to 6 do begin  
        MyRecordRef.Open(i);  
        varCaption := MyRecordRef.Caption;  
        Message(Text000, i, varCaption);  
        MyRecordRef.Close;  
        end;  
end;
```  
  
 This example displays the following:  
  
 **Table No: 3   Caption: Payment terms**  
  
 **Table No: 4   Caption: Currency**  
  
 **Table No: 5   Caption: Finance Charge Terms**  

## See Also
[RecordRef Data Type](recordref-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)