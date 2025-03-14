---
title: "XmlDocument.SetDeclaration(XmlDeclaration) Method"
description: "Sets the XML declaration for this document."
ms.author: solsen
ms.date: 08/26/2024
ms.topic: reference
author: SusanneWindfeldPedersen
ms.reviewer: solsen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# XmlDocument.SetDeclaration(XmlDeclaration) Method
> **Version**: _Available or changed with runtime version 1.0._

Sets the XML declaration for this document.


## Syntax
```AL
[Ok := ]  XmlDocument.SetDeclaration(Declaration: XmlDeclaration)
```
## Parameters
*XmlDocument*  
&emsp;Type: [XmlDocument](xmldocument-data-type.md)  
An instance of the [XmlDocument](xmldocument-data-type.md) data type.  

*Declaration*  
&emsp;Type: [XmlDeclaration](../xmldeclaration/xmldeclaration-data-type.md)  
The new value of the XML declaration of this document.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the operation was successful; otherwise **false**.   If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## Related information
[XmlDocument Data Type](xmldocument-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)