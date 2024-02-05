---
title: "XmlDocumentType.Create(Text, Text, Text, Text) Method"
description: "Creates an XmlDocumentType node."
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
# XmlDocumentType.Create(Text, Text, Text, Text) Method
> **Version**: _Available or changed with runtime version 1.0._

Creates an XmlDocumentType node.


## Syntax
```AL
XmlDocumentType :=   XmlDocumentType.Create(Name: Text, PublicId: Text, SystemId: Text, InternalSubSet: Text)
```
## Parameters
*Name*  
&emsp;Type: [Text](../text/text-data-type.md)  
A string that contains the qualified name of the DTD, which is the same as the qualified name of the root element of the XML document.  

*PublicId*  
&emsp;Type: [Text](../text/text-data-type.md)  
A string that contains the public identifier of an external public DTD.  

*SystemId*  
&emsp;Type: [Text](../text/text-data-type.md)  
A string that contains the system identifier of an external private DTD.  

*InternalSubSet*  
&emsp;Type: [Text](../text/text-data-type.md)  
A string that contains the internal subset for an internal DTD.  


## Return Value
*XmlDocumentType*  
&emsp;Type: [XmlDocumentType](xmldocumenttype-data-type.md)  
The created XmlDocumentType node.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[XmlDocumentType Data Type](xmldocumenttype-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)