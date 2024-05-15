---
title: "SubPageView Property"
description: Describes the SubPageView property in Business Central.
author: jswymer
ms.date: 10/01/2020
ms.reviewer: na
ms.suite: na
ms.topic: article
---

# SubPageView Property

Sets the table view for a part.  

## Syntax
```
SubPageView = [<SORTING>[<KeyList>] [ORDER(Ascending|Descending)] [WHERE(<TableFilters>)]<KeyList> ::= PagePartTableKey1, PagePartTableKey2, <TableFilters> ::= <TableFilter> {,<TableFilter>}<TableFilter> ::= <PagePartTableFieldName>= CONST(<FieldConst>) | FILTER(<FilterExpression>)
```

## Applies to  
  
- Parts
  
## Remarks  

The table view is the view of the table that you present to the user. You determine what records the user can see by setting filters, determining the sorting order, and selecting the keys.  
  
You can use this property to sort the information in the table for display in this part.


## Example

```AL
SubPageView = sorting("No.") where (City=filter('Miami'));
```

For an example of a page part using the `SubPageView` property, see [Adding a FactBox to a Page](../devenv-adding-a-factbox-to-page.md).

## See Also 
 
[Properties](devenv-properties.md)  
[SubPageLink Property](devenv-subpagelink-property.md)  
 