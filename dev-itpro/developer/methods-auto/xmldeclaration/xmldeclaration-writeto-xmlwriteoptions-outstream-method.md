---
title: "XmlDeclaration.WriteTo(XmlWriteOptions, OutStream) Method"
description: "Serializes and saves the current node to the given variable."
ms.author: solsen
ms.date: 08/26/2024
ms.topic: reference
author: SusanneWindfeldPedersen
ms.reviewer: solsen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# XmlDeclaration.WriteTo(XmlWriteOptions, OutStream) Method
> **Version**: _Available or changed with runtime version 1.0._

Serializes and saves the current node to the given variable.


## Syntax
```AL
[Ok := ]  XmlDeclaration.WriteTo(WriteOptions: XmlWriteOptions, OutStream: OutStream)
```
## Parameters
*XmlDeclaration*  
&emsp;Type: [XmlDeclaration](xmldeclaration-data-type.md)  
An instance of the [XmlDeclaration](xmldeclaration-data-type.md) data type.  

*WriteOptions*  
&emsp;Type: [XmlWriteOptions](../xmlwriteoptions/xmlwriteoptions-data-type.md)  
Specifies options for customizing how the node is serialized.  

*OutStream*  
&emsp;Type: [OutStream](../outstream/outstream-data-type.md)  
The OutStream to which you want to save the serialized representation of the node.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the operation was successful; otherwise **false**.   If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## Related information
[XmlDeclaration Data Type](xmldeclaration-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)