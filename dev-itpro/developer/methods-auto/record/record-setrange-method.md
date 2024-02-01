---
title: "Record.SetRange(Any [, Any] [, Any]) Method"
description: "Sets a simple filter, such as a single range or a single value, on a field."
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
# Record.SetRange(Any [, Any] [, Any]) Method
> **Version**: _Available or changed with runtime version 1.0._

Sets a simple filter, such as a single range or a single value, on a field.


## Syntax
```AL
 Record.SetRange(Field: Any [, FromValue: Any] [, ToValue: Any])
```
## Parameters
*Record*  
&emsp;Type: [Record](record-data-type.md)  
An instance of the [Record](record-data-type.md) data type.  

*Field*  
&emsp;Type: [Any](../any/any-data-type.md)  
The field that you want to filter.  

*[Optional] FromValue*  
&emsp;Type: [Any](../any/any-data-type.md)  
The lower limit of the range. The data type of this parameter must match the data type of Field.  

*[Optional] ToValue*  
&emsp;Type: [Any](../any/any-data-type.md)  
The upper limit of the range. If you omit this parameter, then the value that you specified for FromValue is used. The data type of this parameter must match the data type of Field.  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[Record Data Type](record-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)