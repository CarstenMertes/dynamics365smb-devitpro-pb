---
title: "XmlNameTable.Get(Text, var Text) Method"
description: "Gets the atomized string with the specified value."
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
# XmlNameTable.Get(Text, var Text) Method
> **Version**: _Available or changed with runtime version 1.0._

Gets the atomized string with the specified value.


## Syntax
```AL
[Ok := ]  XmlNameTable.Get(Key: Text, var Result: Text)
```
## Parameters
*XmlNameTable*  
&emsp;Type: [XmlNameTable](xmlnametable-data-type.md)  
An instance of the [XmlNameTable](xmlnametable-data-type.md) data type.  

*Key*  
&emsp;Type: [Text](../text/text-data-type.md)  
The string to find.  

*Result*  
&emsp;Type: [Text](../text/text-data-type.md)  
The atomized string object if the string has been atomized.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the key exists, otherwise **false**. If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[XmlNameTable Data Type](xmlnametable-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)