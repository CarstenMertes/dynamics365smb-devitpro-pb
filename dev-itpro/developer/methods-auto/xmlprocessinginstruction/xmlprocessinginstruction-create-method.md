---
title: "XmlProcessingInstruction.Create(Text, Text) Method"
description: "Creates an XmlProcessingInstruction node."
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
# XmlProcessingInstruction.Create(Text, Text) Method
> **Version**: _Available or changed with runtime version 1.0._

Creates an XmlProcessingInstruction node.


## Syntax
```AL
XmlProcessingInstruction :=   XmlProcessingInstruction.Create(Target: Text, Data: Text)
```
## Parameters
*Target*  
&emsp;Type: [Text](../text/text-data-type.md)  
The target of the processing instruction.  

*Data*  
&emsp;Type: [Text](../text/text-data-type.md)  
The content of the processing instruction, excluding the target.  


## Return Value
*XmlProcessingInstruction*  
&emsp;Type: [XmlProcessingInstruction](xmlprocessinginstruction-data-type.md)  
The created XmlProcessingInstruction node.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[XmlProcessingInstruction Data Type](xmlprocessinginstruction-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)