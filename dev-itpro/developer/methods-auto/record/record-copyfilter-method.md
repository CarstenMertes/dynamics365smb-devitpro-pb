---
title: "Record.CopyFilter(Any, Any) Method"
description: "Copies the filter that has been set for one field and applies it to another field."
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
# Record.CopyFilter(Any, Any) Method
> **Version**: _Available or changed with runtime version 1.0._

Copies the filter that has been set for one field and applies it to another field.


## Syntax
```AL
 Record.CopyFilter(FromField: Any, Record.ToField: Any)
```
## Parameters
*Record*  
&emsp;Type: [Record](record-data-type.md)  
An instance of the [Record](record-data-type.md) data type.  

*FromField*  
&emsp;Type: [Any](../any/any-data-type.md)  
The field from which the filter will be copied.  

*Record.ToField*  
&emsp;Type: [Any](../any/any-data-type.md)  
  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks
The filter is copied and remains in the assigned group number. For example: `Rec.CopyFilter(FromRec);`
disregards the current filter group on both `Rec` and `FromRec`, and copies the filter in `FromRec` (regardless of group number) into the same filter group assignment on `Rec`.

## See Also
[Record Data Type](record-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)