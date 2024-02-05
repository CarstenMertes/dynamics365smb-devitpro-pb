---
title: "XmlDocumentType.SetName(Text) Method"
description: "Sets the name for this Document Type Definition (DTD)."
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
# XmlDocumentType.SetName(Text) Method
> **Version**: _Available or changed with runtime version 1.0._

Sets the name for this Document Type Definition (DTD).


## Syntax
```AL
[Ok := ]  XmlDocumentType.SetName(Value: Text)
```
## Parameters
*XmlDocumentType*  
&emsp;Type: [XmlDocumentType](xmldocumenttype-data-type.md)  
An instance of the [XmlDocumentType](xmldocumenttype-data-type.md) data type.  

*Value*  
&emsp;Type: [Text](../text/text-data-type.md)  
A string that contains the new name for this Document Type Definition (DTD).  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the operation was successful; otherwise **false**.   If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[XmlDocumentType Data Type](xmldocumenttype-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)