---
title: "Record.GetRangeMax(Any) Method"
description: "Gets the maximum value in a range for a field."
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
# Record.GetRangeMax(Any) Method
> **Version**: _Available or changed with runtime version 1.0._

Gets the maximum value in a range for a field.


## Syntax
```AL
Value :=   Record.GetRangeMax(Field: Any)
```
## Parameters
*Record*  
&emsp;Type: [Record](record-data-type.md)  
An instance of the [Record](record-data-type.md) data type.  

*Field*  
&emsp;Type: [Any](../any/any-data-type.md)  
The field for which you want to find the maximum value. The current filter on Field must be a single range filter; otherwise, a run-time error occurs.  


## Return Value
*Value*  
&emsp;Type: [Any](../any/any-data-type.md)  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[Record Data Type](record-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)