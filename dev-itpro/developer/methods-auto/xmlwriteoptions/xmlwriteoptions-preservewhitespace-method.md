---
title: "XmlWriteOptions.PreserveWhitespace([Boolean]) Method"
description: "Gets or sets a value that indicates whether insignificant white space should be preserved during serialization."
ms.author: solsen
ms.custom: na
ms.date: 07/07/2021
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# XmlWriteOptions.PreserveWhitespace([Boolean]) Method
> **Version**: _Available or changed with runtime version 1.0._

Gets or sets a value that indicates whether insignificant white space should be preserved during serialization.


## Syntax
```AL
[Value := ]  XmlWriteOptions.PreserveWhitespace([NewValue: Boolean])
```
> [!NOTE]
> This method can be invoked using property access syntax.
## Parameters
*XmlWriteOptions*  
&emsp;Type: [XmlWriteOptions](xmlwriteoptions-data-type.md)  
An instance of the [XmlWriteOptions](xmlwriteoptions-data-type.md) data type.  

*[Optional] NewValue*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
The new value of the flag.  


## Return Value
*[Optional] Value*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if insignificant white spaces should be preserved during serialization, otherwise **false**.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[XmlWriteOptions Data Type](xmlwriteoptions-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)