---
title: "XmlNamespaceManager.LookupPrefix(Text, var Text) Method"
description: "Finds the prefix declared for the given namespace URI."
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
# XmlNamespaceManager.LookupPrefix(Text, var Text) Method
> **Version**: _Available or changed with runtime version 1.0._

Finds the prefix declared for the given namespace URI.


## Syntax
```AL
[Ok := ]  XmlNamespaceManager.LookupPrefix(Uri: Text, var Result: Text)
```
## Parameters
*XmlNamespaceManager*  
&emsp;Type: [XmlNamespaceManager](xmlnamespacemanager-data-type.md)  
An instance of the [XmlNamespaceManager](xmlnamespacemanager-data-type.md) data type.  

*Uri*  
&emsp;Type: [Text](../text/text-data-type.md)  
The namespace to resolve for the prefix.  

*Result*  
&emsp;Type: [Text](../text/text-data-type.md)  
The matching prefix. If there is no mapped prefix, the method returns an empty string.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the operation was successful; otherwise **false**.   If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[XmlNamespaceManager Data Type](xmlnamespacemanager-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)