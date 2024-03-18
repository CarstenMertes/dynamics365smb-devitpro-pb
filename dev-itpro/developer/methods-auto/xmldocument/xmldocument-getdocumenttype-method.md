---
title: "XmlDocument.GetDocumentType(var XmlDocumentType) Method"
description: "Gets the Document Type Definition (DTD) for this document."
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
# XmlDocument.GetDocumentType(var XmlDocumentType) Method
> **Version**: _Available or changed with runtime version 1.0._

Gets the Document Type Definition (DTD) for this document.


## Syntax
```AL
[Ok := ]  XmlDocument.GetDocumentType(var DocumentType: XmlDocumentType)
```
## Parameters
*XmlDocument*  
&emsp;Type: [XmlDocument](xmldocument-data-type.md)  
An instance of the [XmlDocument](xmldocument-data-type.md) data type.  

*DocumentType*  
&emsp;Type: [XmlDocumentType](../xmldocumenttype/xmldocumenttype-data-type.md)  
The Document Type Definition (DTD) for this document.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the operation was successful; otherwise **false**.   If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[XmlDocument Data Type](xmldocument-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)