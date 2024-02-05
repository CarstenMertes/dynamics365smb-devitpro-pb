---
title: "FilterPageBuilder.Name(Integer) Method"
description: "Gets the name of a table filter control that is included on a filter page based on an index number that is assigned to the filter control."
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
# FilterPageBuilder.Name(Integer) Method
> **Version**: _Available or changed with runtime version 1.0._

Gets the name of a table filter control that is included on a filter page based on an index number that is assigned to the filter control.


## Syntax
```AL
Name :=   FilterPageBuilder.Name(Index: Integer)
```
## Parameters
*FilterPageBuilder*  
&emsp;Type: [FilterPageBuilder](filterpagebuilder-data-type.md)  
An instance of the [FilterPageBuilder](filterpagebuilder-data-type.md) data type.  

*Index*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The index of a filter control. The value must be in the range 1 to N, where N is the number of filter controls on the filter page.  


## Return Value
*Name*  
&emsp;Type: [Text](../text/text-data-type.md)  
The name of the filter control.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Example  
 The following example initializes a filter page object that includes two filter controls for the **Date** system table. The NAME method returns the names of filter control in a message dialog box.  
 
```al
    var
        varDateItem: Text[30];
        varCount: Integer;
        varIndex: Integer;
        varFilterPageBuilder: FilterPageBuilder;

    begin
        varDateItem := 'Date record';
        varFilterPageBuilder.AddTable(varDateItem + ' 1', Database::Date);
        varFilterPageBuilder.AddTable(varDateItem + ' 2', Database::Date);
        varCount := varFilterPageBuilder.COUNT;
        if varCount <> 2 then
            Error('There should be two controls in FilterPageBuilder');
        for varIndex := 1 to varCount do
            Message('Control item %1 is named %2', varIndex, varFilterPageBuilder.Name(varIndex));
        varFilterPageBuilder.RunModal();
    end;
    
```  
  

## See Also
[FilterPageBuilder Data Type](filterpagebuilder-data-type.md)  
[Creating Filter Pages for Tables](../../devenv-filter-pages-for-filtering-tables.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)