---
title: "GridLayout Property"
description: "Specifies if the layout is rows or columns."
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
# GridLayout Property
> **Version**: _Available or changed with runtime version 1.0._

Specifies if the layout is rows or columns.

## Applies to
-   Page Group

## Property Value

|Value|Available or changed with|Description|
|-----------|-----------|---------------------------------------|
|**Rows**|runtime version 1.0|Use rows for the layout.|
|**Columns**|runtime version 1.0|Use columns for the layout.|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Syntax

```AL
GridLayout = Columns;
```
  
## Remarks 

> [NOTE]
> The controls inside this definition should be laid out as a grid using the caption of the first group as row caption. 

By default, fields in a FastTab on a page are arranged automatically in two columns that are based on the number of fields. You use a Grid control to customize the arrangement of fields into rows and columns, and design it to look like a grid-like format or a matrix-like format. For more information, see [Arranging Fields in Rows and Columns Using the Grid Control](../devenv-arrange-fields-in-rows-and-columns-using-gridlayout-control.md).
 
This property is only supported on grids.

> [!IMPORTANT]
> Arranging in rows only works in the [!INCLUDE[nav_windows_md](../includes/nav_windows_md.md)]. In the [!INCLUDE[webclient](../includes/webclient.md)], fields can only be arranged in columns.

## See Also

[Field Arrangement on FastTabs](../devenv-arranging-fields-on-fasttab.md)  
[Properties](devenv-properties.md)