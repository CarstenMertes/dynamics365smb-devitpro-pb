---
title: "XmlComment.WriteTo(var Text) Method"
description: "Serializes and saves the current node to the given variable."
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
# XmlComment.WriteTo(var Text) Method
> **Version**: _Available or changed with runtime version 1.0._

Serializes and saves the current node to the given variable.


## Syntax
```AL
[Ok := ]  XmlComment.WriteTo(var Text: Text)
```
## Parameters
*XmlComment*  
&emsp;Type: [XmlComment](xmlcomment-data-type.md)  
An instance of the [XmlComment](xmlcomment-data-type.md) data type.  

*Text*  
&emsp;Type: [Text](../text/text-data-type.md)  
The Text variable to which you want to save the serialized representation of the node.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the operation was successful; otherwise **false**.   If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[XmlComment Data Type](xmlcomment-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)