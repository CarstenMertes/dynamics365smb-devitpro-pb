---
title: "XmlNode.AsXmlDocument() Method"
description: "Converts the node to an XmlDocument node."
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
# XmlNode.AsXmlDocument() Method
> **Version**: _Available or changed with runtime version 1.0._

Converts the node to an XmlDocument node. The operation will fail if the node is not an XmlDocument.


## Syntax
```AL
XmlDocument :=   XmlNode.AsXmlDocument()
```

## Parameters
*XmlNode*  
&emsp;Type: [XmlNode](xmlnode-data-type.md)  
An instance of the [XmlNode](xmlnode-data-type.md) data type.  

## Return Value
*XmlDocument*  
&emsp;Type: [XmlDocument](../xmldocument/xmldocument-data-type.md)  
An XmlDocument value that references the current XmlNode.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[XmlNode Data Type](xmlnode-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)