---
title: "XmlDocument.GetRoot(var XmlElement) Method"
description: "Gets the root element of the XML tree for this document."
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
# XmlDocument.GetRoot(var XmlElement) Method
> **Version**: _Available or changed with runtime version 1.0._

Gets the root element of the XML tree for this document.


## Syntax
```AL
[Ok := ]  XmlDocument.GetRoot(var Result: XmlElement)
```
## Parameters
*XmlDocument*  
&emsp;Type: [XmlDocument](xmldocument-data-type.md)  
An instance of the [XmlDocument](xmldocument-data-type.md) data type.  

*Result*  
&emsp;Type: [XmlElement](../xmlelement/xmlelement-data-type.md)  
The root element of the XML tree for this document.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the operation was successful; otherwise **false**.   If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[XmlDocument Data Type](xmldocument-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)