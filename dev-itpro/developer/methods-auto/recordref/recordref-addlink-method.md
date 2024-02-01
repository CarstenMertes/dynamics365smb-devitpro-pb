---
title: "RecordRef.AddLink(Text [, Text]) Method"
description: "Adds a link to a record in a table."
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
# RecordRef.AddLink(Text [, Text]) Method
> **Version**: _Available or changed with runtime version 1.0._

Adds a link to a record in a table.


## Syntax
```AL
[ID := ]  RecordRef.AddLink(URL: Text [, Description: Text])
```
## Parameters
*RecordRef*  
&emsp;Type: [RecordRef](recordref-data-type.md)  
An instance of the [RecordRef](recordref-data-type.md) data type.  

*URL*  
&emsp;Type: [Text](../text/text-data-type.md)  
The link that you want to add to the record.  

*[Optional] Description*  
&emsp;Type: [Text](../text/text-data-type.md)  
Optional description of the link.  


## Return Value
*[Optional] ID*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The ID of the URL that you want to add to the record. Every time that you add a link to a page or a table, an entry is created in the Record Link system table. Each entry is given an ID.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  
 The URL can be a link to a Web site, a file stored on the local or on a remote computer, or a link to a [!INCLUDE[d365fin_md](../../includes/d365fin_md.md)] page. You can then view the link in the **Links** FactBox on pages that display the record.  

## Example  
 The following example adds a link to a record in the Customer table. The code starts by opening table 18 \(Customer) as a RecordRef variable that is named CustomerRecref. The [Field Method (RecordRef)](recordref-field-method.md) creates a FieldRef variable that is named MyFieldRef for the first field \(No.\). Next, `MyFieldRef.Value` is set to record 01121212. The [Find Method (RecordRef)](recordref-find-method.md) method searches the records for record no. 01121212. If the record is found, then the AddLink method adds a link to the record. The link is assigned a link ID, which is stored in the LinkID variable. The link ID is displayed in a message box. You can view the link you added in the **Links** FactBox on the Customer List or Customer Card pages. 

```al
var
    CustomerNum: Code;
    varLink: Text;
    CustomerRecref: RecordRef;
    MyFieldRef: FieldRef;
    LinkID: Integer;
    Text000: Label 'The link with ID %1 has been added.';
    Text001: Label 'The customer cannot be found.';
begin  
    CustomerNum := '01121212';  
    CustomerRecref.Open(18);  
    MyFieldRef := CustomerRecref.Field(1);  
    MyFieldRef.Value := CustomerNum;  
    if CustomerRecref.Find('=') then begin  
      LinkID := CustomerRecref.AddLink(varLink);  
      Message(Text000, LinkID);  
    end else
      Message(Text001);  
end;
```  

## See Also
[RecordRef Data Type](recordref-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)