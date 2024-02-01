---
title: "SubPageLink Property"
description: "Sets a link to a Factbox from a page."
ms.author: solsen
ms.custom: na
ms.date: 06/15/2022
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# SubPageLink Property
> **Version**: _Available or changed with runtime version 1.0._

Sets a link to a Factbox from a page.
The following syntax is valid for the SubPageLink property:

```
SubPageLink = <TableFilters>
<TableFilters> ::= <TableFilter> {,<TableFilter>}
<TableFilter> ::= <PagePartTableFieldName> = CONST(<FieldConst>) | FILTER(<Filter>) | FIELD(<SourceFieldName>) |
FIELD(UPPERLIMIT(<SourceFieldName>)) | FIELD(FILTER(<SourceFieldName>)) | FIELD(UPPERLIMIT(FILTER(<SourceFieldName>)))
```


## Applies to
-   Page Part
-   Page System Part
-   Page Chart Part

[//]: # (IMPORTANT: END>DO_NOT_EDIT)


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