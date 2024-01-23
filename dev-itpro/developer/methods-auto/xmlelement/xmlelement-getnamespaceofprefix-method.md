---
title: "XmlElement.GetNamespaceOfPrefix(Text, var Text) Method"
description: "Gets the namespace associated with a particular prefix for this element."
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
# XmlElement.GetNamespaceOfPrefix(Text, var Text) Method
> **Version**: _Available or changed with runtime version 1.0._

Gets the namespace associated with a particular prefix for this element.


## Syntax
```AL
[Ok := ]  XmlElement.GetNamespaceOfPrefix(Prefix: Text, var Result: Text)
```
## Parameters
*XmlElement*  
&emsp;Type: [XmlElement](xmlelement-data-type.md)  
An instance of the [XmlElement](xmlelement-data-type.md) data type.  

*Prefix*  
&emsp;Type: [Text](../text/text-data-type.md)  
A string that contains the namespace prefix to look up.  

*Result*  
&emsp;Type: [Text](../text/text-data-type.md)  
The namespace URI associated with the given prefix for this element.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the operation was successful; otherwise **false**.   If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[XmlElement Data Type](xmlelement-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)