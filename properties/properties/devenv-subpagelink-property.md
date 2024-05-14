---
title: "SubPageLink Property"
ms.date: 10/01/2020
ms.reviewer: na
ms.suite: na
ms.topic: article
---

# SubPageLink Property

Sets a link to a Factbox from a page.

## Syntax

```
SubPageLink = <TableFilters> ::= <TableFilter> {,<TableFilter>} <TableFilter> ::= <PagePartTableFieldName> = CONST(<FieldConst>) | FILTER(<Filter>) | FIELD (<SourceFieldName>) | FIELD(UPPERLIMIT(<SourceFieldName>)) | FIELD(FILTER(<SourceFieldName>)) | FIELD(UPPERLIMIT(FILTER(<SourceFieldName>)))
```  
  
## Applies to  
  
- Parts  

## Syntax example

```AL
area(factboxes)
{
    part(MyControl;Id)
    {
        ApplicationArea = All;
        SubPageLink = "Table ID" = const(36),"Document Type" = field("Document Type"),"Document No." = field("No.");
    }
}
    
```
  
## Remarks  

The link is updated when the current record changes.  
  
For an example of how to use `SubPageLink` to update the content of a FactBox in the client as different items are selected in a list page. <!-- See [Walkthrough: Adding a FactBox to the Customer List Page](../devenv-Walkthrough-Adding-a-FactBox-to-the-Customer-List-Page.md).  -->
  
## See Also  

[Properties](devenv-properties.md)  
[SubPageView Property](devenv-subpageview-property.md)