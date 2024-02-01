---
title: "XmlNameTable.Add(Text) Method"
description: "Atomizes the specified string and adds it to the XmlNameTable."
ms.author: solsen
ms.custom: na
ms.date: 03/24/2022
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# XmlNameTable.Add(Text) Method
> **Version**: _Available or changed with runtime version 1.0._

Atomizes the specified string and adds it to the XmlNameTable.


## Syntax
```AL
[AddedKey := ]  XmlNameTable.Add(Key: Text)
```
## Parameters
*XmlNameTable*  
&emsp;Type: [XmlNameTable](xmlnametable-data-type.md)  
An instance of the [XmlNameTable](xmlnametable-data-type.md) data type.  

*Key*  
&emsp;Type: [Text](../text/text-data-type.md)  
The string to add.  


## Return Value
*[Optional] AddedKey*  
&emsp;Type: [Text](../text/text-data-type.md)  
The new atomized string or the existing one if it already exists


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[XmlNameTable Data Type](xmlnametable-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)