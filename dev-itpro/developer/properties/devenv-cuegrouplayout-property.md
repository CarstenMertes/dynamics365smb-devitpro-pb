---
title: "CuegroupLayout Property"
description: "Specifies if the layout is wide."
ms.author: solsen
ms.custom: na
ms.date: 12/08/2022
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# CuegroupLayout Property
> **Version**: _Available or changed with runtime version 1.0._

Specifies if the layout is wide.

## Applies to
-   Page Group

## Property Value

|Value|Available or changed with|Description|
|-----------|-----------|---------------------------------------|
|**Wide**|runtime version 1.0|Sets the `cuegroup` control to the wide layout|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Syntax

```AL
CuegroupLayout = wide;
```
  
## Remarks  
For more information about the wide layout for Cues, see [Normal and wide layout for Cues](../devenv-cues-action-tiles.md#CueWideLayout).

## Example

```AL
cuegroup(SalesCueContainer)
{
    CaptionML=ENU='Sales Invoices';
    CuegroupLayout=wide;
    field(SalesCue; SalesInvoicesOpen)
    {
        CaptionML=ENU='Open';
        DrillDownPageId="Sales Invoice List";
    }
} 
```
  
## See Also

[Properties](devenv-properties.md)
[Rowspan Property](devenv-rowspan-property.md)  
[Columnspan Property](devenv-columnspan-property.md)