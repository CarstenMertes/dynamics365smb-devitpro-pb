---
title: "XmlNamespaceManager.NameTable([XmlNameTable]) Method"
description: "Gets or sets the XmlNameTable associated with this object."
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
# XmlNamespaceManager.NameTable([XmlNameTable]) Method
> **Version**: _Available or changed with runtime version 1.0._

Gets or sets the XmlNameTable associated with this object.


## Syntax
```AL
[Value := ]  XmlNamespaceManager.NameTable([NewValue: XmlNameTable])
```
> [!NOTE]
> This method can be invoked using property access syntax.
## Parameters
*XmlNamespaceManager*  
&emsp;Type: [XmlNamespaceManager](xmlnamespacemanager-data-type.md)  
An instance of the [XmlNamespaceManager](xmlnamespacemanager-data-type.md) data type.  

*[Optional] NewValue*  
&emsp;Type: [XmlNameTable](../xmlnametable/xmlnametable-data-type.md)  
The new XmlNameTable to associate with this object. Setting the NameTable will reset the state of the XmlNamespaceManager.  


## Return Value
*[Optional] Value*  
&emsp;Type: [XmlNameTable](../xmlnametable/xmlnametable-data-type.md)  
The XmlNameTable associated with this object.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[XmlNamespaceManager Data Type](xmlnamespacemanager-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)