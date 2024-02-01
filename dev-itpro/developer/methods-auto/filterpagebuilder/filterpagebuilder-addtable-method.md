---
title: "FilterPageBuilder.AddTable(Text, Integer) Method"
description: "Adds filter control for a table to a filter page."
ms.author: solsen
ms.custom: na
ms.date: 03/02/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# FilterPageBuilder.AddTable(Text, Integer) Method
> **Version**: _Available or changed with runtime version 1.0._

Adds filter control for a table to a filter page.


## Syntax
```AL
[Name := ]  FilterPageBuilder.AddTable(Name: Text, TableNo: Integer)
```
## Parameters
*FilterPageBuilder*  
&emsp;Type: [FilterPageBuilder](filterpagebuilder-data-type.md)  
An instance of the [FilterPageBuilder](filterpagebuilder-data-type.md) data type.  

*Name*  
&emsp;Type: [Text](../text/text-data-type.md)  
Assigns a name to the filter control for the table. The text displays as the caption for the filter control on the rendered filter page in the client.  

*TableNo*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The ID of the table object that you want to filter on.  


## Return Value
*[Optional] Name*  
&emsp;Type: [Text](../text/text-data-type.md)  
The text that is specified by the Name parameter. If an error occurs at runtime, an empty text string is returned. If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  
 In the filter page that is rendered in the client, the AddTable method defines a filter control for the specified table where the user can set filters on specific fields in the table.  

 You can use the **AddField Method** or [AddFieldNo Method](../../methods-auto/filterpagebuilder/filterpagebuilder-addfieldno-method.md) method to add field of the table to the filter control.  

## Example  
 The following example initializes a filter page object that includes a filter control that uses the Date system table. The filter control has the caption of **Date record**.  

```al
var
    varDateItem: Text[30];
    varFilterPageBuilder: FilterPageBuilder;

begin
    varDateItem := 'Date record';  
    varFilterPageBuilder.AddTable(varDateItem, Database::Date);
    varFilterPageBuilder.RunModal(); 
end;
```  

## See Also
[FilterPageBuilder Data Type](filterpagebuilder-data-type.md)  
[Creating Filter Pages for Tables](../../devenv-filter-pages-for-filtering-tables.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)