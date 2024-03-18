---
title: "FilterPageBuilder.PageCaption([Text]) Method"
description: "Gets or sets the FilterPageBuilder UI caption."
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
# FilterPageBuilder.PageCaption([Text]) Method
> **Version**: _Available or changed with runtime version 1.0._

Gets or sets the FilterPageBuilder UI caption. Defaults to the resource text if not explicitly set.


## Syntax
```AL
[PageCaption := ]  FilterPageBuilder.PageCaption([PageCaption: Text])
```
> [!NOTE]
> This method can be invoked using property access syntax.
## Parameters
*FilterPageBuilder*  
&emsp;Type: [FilterPageBuilder](filterpagebuilder-data-type.md)  
An instance of the [FilterPageBuilder](filterpagebuilder-data-type.md) data type.  

*[Optional] PageCaption*  
&emsp;Type: [Text](../text/text-data-type.md)  
The value to set for the FilterPageBuilder UI caption.  


## Return Value
*[Optional] PageCaption*  
&emsp;Type: [Text](../text/text-data-type.md)  
The current value of the FilterPageBuilder UI caption.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Example

```al
var
    varFilterPageBuilder: FilterPageBuilder;
    Customer: Record Customer;
    Item: Record Item;
    varDateItem: Text[30];
begin
    varFilterPageBuilder.AddRecord('Item Table', Item);  
    varFilterPageBuilder.Addfield('Item Table', Item."No.", '>100');  
    varFilterPageBuilder.PageCaption := 'Item Filter Page';
    varFilterPageBuilder.RunModal;  
    Item.SetView(varFilterPageBuilder.Getview('Item Table')); 
end;
```

## See Also
[FilterPageBuilder Data Type](filterpagebuilder-data-type.md)  
[Creating Filter Pages for Tables](../../devenv-filter-pages-for-filtering-tables.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)