---
title: "XmlNode.AsXmlText() Method"
description: "Converts the node to an XmlText node."
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
# XmlNode.AsXmlText() Method
> **Version**: _Available or changed with runtime version 1.0._

Converts the node to an XmlText node. The operation will fail if the node is not an XmlText.


## Syntax
```AL
XmlText :=   XmlNode.AsXmlText()
```

## Parameters
*XmlNode*  
&emsp;Type: [XmlNode](xmlnode-data-type.md)  
An instance of the [XmlNode](xmlnode-data-type.md) data type.  

## Return Value
*XmlText*  
&emsp;Type: [XmlText](../xmltext/xmltext-data-type.md)  
An XmlText value that references the current XmlNode.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[XmlNode Data Type](xmlnode-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)