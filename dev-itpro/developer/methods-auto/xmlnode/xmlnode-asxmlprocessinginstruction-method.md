---
title: "XmlNode.AsXmlProcessingInstruction() Method"
description: "Converts the node to an XmlProcessingInstruction node."
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
# XmlNode.AsXmlProcessingInstruction() Method
> **Version**: _Available or changed with runtime version 1.0._

Converts the node to an XmlProcessingInstruction node. The operation will fail if the node is not an XmlProcessingInstruction.


## Syntax
```AL
XmlProcessingInstruction :=   XmlNode.AsXmlProcessingInstruction()
```

## Parameters
*XmlNode*  
&emsp;Type: [XmlNode](xmlnode-data-type.md)  
An instance of the [XmlNode](xmlnode-data-type.md) data type.  

## Return Value
*XmlProcessingInstruction*  
&emsp;Type: [XmlProcessingInstruction](../xmlprocessinginstruction/xmlprocessinginstruction-data-type.md)  
An XmlProcessingInstruction value that references the current XmlNode.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[XmlNode Data Type](xmlnode-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)