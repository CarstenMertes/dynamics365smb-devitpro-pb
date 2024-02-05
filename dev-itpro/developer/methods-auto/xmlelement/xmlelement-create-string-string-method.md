---
title: "XmlElement.Create(Text, Text) Method"
description: "Creates an XmlElement node."
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
# XmlElement.Create(Text, Text) Method
> **Version**: _Available or changed with runtime version 1.0._

Creates an XmlElement node.


## Syntax
```AL
XmlElement :=   XmlElement.Create(LocalName: Text, NamespaceUri: Text)
```
## Parameters
*LocalName*  
&emsp;Type: [Text](../text/text-data-type.md)  
The local name of the element to create.  

*NamespaceUri*  
&emsp;Type: [Text](../text/text-data-type.md)  
The namespace URI of the element to create.  


## Return Value
*XmlElement*  
&emsp;Type: [XmlElement](xmlelement-data-type.md)  
The created XmlElement node.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[XmlElement Data Type](xmlelement-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)