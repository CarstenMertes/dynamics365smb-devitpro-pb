---
title: "XmlDocument.ReadFrom(Text, var XmlDocument) Method"
description: "Reads and parses the XML document from the given data source."
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
# XmlDocument.ReadFrom(Text, var XmlDocument) Method
> **Version**: _Available or changed with runtime version 1.0._

Reads and parses the XML document from the given data source.


## Syntax
```AL
[Ok := ]  XmlDocument.ReadFrom(Text: Text, var Result: XmlDocument)
```
## Parameters
*Text*  
&emsp;Type: [Text](../text/text-data-type.md)  
A string containing an XML document.  

*Result*  
&emsp;Type: [XmlDocument](xmldocument-data-type.md)  
The XmlDocument parsed from the given data source.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the operation was successful; otherwise **false**.   If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[XmlDocument Data Type](xmldocument-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)