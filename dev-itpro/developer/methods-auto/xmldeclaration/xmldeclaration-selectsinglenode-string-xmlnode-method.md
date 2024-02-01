---
title: "XmlDeclaration.SelectSingleNode(Text, var XmlNode) Method"
description: "Selects the first XmlNode that matches the XPath expression."
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
# XmlDeclaration.SelectSingleNode(Text, var XmlNode) Method
> **Version**: _Available or changed with runtime version 1.0._

Selects the first XmlNode that matches the XPath expression.


## Syntax
```AL
[Ok := ]  XmlDeclaration.SelectSingleNode(XPath: Text, var Node: XmlNode)
```
## Parameters
*XmlDeclaration*  
&emsp;Type: [XmlDeclaration](xmldeclaration-data-type.md)  
An instance of the [XmlDeclaration](xmldeclaration-data-type.md) data type.  

*XPath*  
&emsp;Type: [Text](../text/text-data-type.md)  
The XPath expression.  

*Node*  
&emsp;Type: [XmlNode](../xmlnode/xmlnode-data-type.md)  
The first XmlNode that matches the XPath query.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the operation was successful; otherwise **false**.   If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[XmlDeclaration Data Type](xmldeclaration-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)