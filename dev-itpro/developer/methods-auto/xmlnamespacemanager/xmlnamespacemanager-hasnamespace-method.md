---
title: "XmlNamespaceManager.HasNamespace(Text) Method"
description: "Gets a value indicating whether the supplied prefix has a namespace defined for the current scope."
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
# XmlNamespaceManager.HasNamespace(Text) Method
> **Version**: _Available or changed with runtime version 1.0._

Gets a value indicating whether the supplied prefix has a namespace defined for the current scope.


## Syntax
```AL
HasNamespace :=   XmlNamespaceManager.HasNamespace(Prefix: Text)
```
## Parameters
*XmlNamespaceManager*  
&emsp;Type: [XmlNamespaceManager](xmlnamespacemanager-data-type.md)  
An instance of the [XmlNamespaceManager](xmlnamespacemanager-data-type.md) data type.  

*Prefix*  
&emsp;Type: [Text](../text/text-data-type.md)  
The prefix of the namespace you want to find.  


## Return Value
*HasNamespace*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the supplied prefix has a namespace defined for the current scope, otherwise **false**.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[XmlNamespaceManager Data Type](xmlnamespacemanager-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)