---
title: "XmlComment.Remove() Method"
description: "Removes this node from its parent element."
ms.author: solsen
ms.date: 08/26/2024
ms.topic: reference
author: SusanneWindfeldPedersen
ms.reviewer: solsen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# XmlComment.Remove() Method
> **Version**: _Available or changed with runtime version 1.0._

Removes this node from its parent element.


## Syntax
```AL
[Ok := ]  XmlComment.Remove()
```
## Parameters
*XmlComment*  
&emsp;Type: [XmlComment](xmlcomment-data-type.md)  
An instance of the [XmlComment](xmlcomment-data-type.md) data type.  

## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the operation was successful; otherwise **false**.   If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## Related information
[XmlComment Data Type](xmlcomment-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)