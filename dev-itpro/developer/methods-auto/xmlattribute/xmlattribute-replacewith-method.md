---
title: "XmlAttribute.ReplaceWith(Any,...) Method"
description: "Replaces this node with the specified content."
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
# XmlAttribute.ReplaceWith(Any,...) Method
> **Version**: _Available or changed with runtime version 1.0._

Replaces this node with the specified content.


## Syntax
```AL
[Ok := ]  XmlAttribute.ReplaceWith(Node: Any,...)
```
## Parameters
*XmlAttribute*  
&emsp;Type: [XmlAttribute](xmlattribute-data-type.md)  
An instance of the [XmlAttribute](xmlattribute-data-type.md) data type.  

*Node*  
&emsp;Type: [Any](../any/any-data-type.md)  
The content with which to replace the current node.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the operation was successful; otherwise **false**.   If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[XmlAttribute Data Type](xmlattribute-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)