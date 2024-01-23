---
title: "Record.CopyFilters(var Record) Method"
description: "Copies all the filters set by the SETFILTER method (Record) or the SETRANGE method (Record) from one record to another."
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
# Record.CopyFilters(var Record) Method
> **Version**: _Available or changed with runtime version 1.0._

Copies all the filters set by the SETFILTER method (Record) or the SETRANGE method (Record) from one record to another.


## Syntax
```AL
 Record.CopyFilters(var FromRecord: Record)
```
## Parameters
*Record*  
&emsp;Type: [Record](record-data-type.md)  
An instance of the [Record](record-data-type.md) data type.  

*FromRecord*  
&emsp;Type: [Record](record-data-type.md)  
The record from which you want to copy filters.  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks
All filters are copied and remain in their assigned group numbers. For example: `Rec.CopyFilters(FromRec);`
disregards the current filter group on both `Rec` and `FromRec`, and copies all filters in `FromRec` (regardless of group number) into the same filter group assignments on `Rec`.

## See Also
[Record Data Type](record-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)