---
title: "RecordRef.ChangeCompany([Text]) Method"
description: "Redirects references to table data from one company to another."
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
# RecordRef.ChangeCompany([Text]) Method
> **Version**: _Available or changed with runtime version 1.0._

Redirects references to table data from one company to another.


## Syntax
```AL
[Ok := ]  RecordRef.ChangeCompany([CompanyName: Text])
```
## Parameters
*RecordRef*  
&emsp;Type: [RecordRef](recordref-data-type.md)  
An instance of the [RecordRef](recordref-data-type.md) data type.  

*[Optional] CompanyName*  
&emsp;Type: [Text](../text/text-data-type.md)  
The name of the company to which you want to change. If you omit this parameter, you change back to the current company.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the operation was successful; otherwise **false**.   If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  
When executing this method, the user's access rights are respected. For example, a user cannot access data in *CompanyName* unless they already have the necessary access rights.  

The **ChangeCompany** method is not affected by the [Reset Method (RecordRef)](recordref-reset-method.md). You can deselect a company by making a new call to **ChangeCompany** or by using the [Clear Method](../system/system-clear-joker-method.md).  

Global filters always belong to a specific company. If you use the following code to select the company named NewCompany, any filters assigned to *RecordRef* will be transferred to *RecordRef* in the new company.  

```al
RecordRef.ChangeCompany(NewCompany);  
```  

Even if you run the **ChangeCompany** method, triggers still run in the current company, not in the company that you specified in the **ChangeCompany** method.  

## Example  
This example shows how to use the **ChangeCompany** method. The following code takes a RecordRef to table **18 Customer** in the current company and redirects it to the table in another company \(in this case Company B\). The last record in the Customer table of Company B is then deleted.  

```al
var
    RecID: RecordID;
    MyRecordRef: RecordRef;
    Text000: Label 'Record to be deleted: %1';
begin
    MyRecordRef.Open(18);  
    MyRecordRef.ChangeCompany('Company B');  
    MyRecordRef.FindLast;  
    RecID := MyRecordRef.RecordId;  
    Message(Text000, RecID);  
    MyRecordRef.Delete;  
end;
```  

## See Also
[RecordRef Data Type](recordref-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)
