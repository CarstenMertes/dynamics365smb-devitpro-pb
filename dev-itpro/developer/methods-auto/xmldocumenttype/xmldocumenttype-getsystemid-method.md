---
title: "XmlDocumentType.GetSystemId(var Text) Method"
description: "Gets the system identifier for this Document Type Definition (DTD)."
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
# XmlDocumentType.GetSystemId(var Text) Method
> **Version**: _Available or changed with runtime version 1.0._

Gets the system identifier for this Document Type Definition (DTD).


## Syntax
```AL
[Ok := ]  XmlDocumentType.GetSystemId(var Result: Text)
```
## Parameters
*XmlDocumentType*  
&emsp;Type: [XmlDocumentType](xmldocumenttype-data-type.md)  
An instance of the [XmlDocumentType](xmldocumenttype-data-type.md) data type.  

*Result*  
&emsp;Type: [Text](../text/text-data-type.md)  
A string that contains the system identifier for this Document Type Definition (DTD).  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the operation was successful; otherwise **false**.   If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[XmlDocumentType Data Type](xmldocumenttype-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)