---
title: "TextBuilder.AppendLine([Text]) Method"
description: "Appends a copy of the specified string followed by the default line terminator to the end of the current TextBuilder object."
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
# TextBuilder.AppendLine([Text]) Method
> **Version**: _Available or changed with runtime version 1.0._

Appends a copy of the specified string followed by the default line terminator to the end of the current TextBuilder object. If this parameter is omitted, only the line terminator will be appended.


## Syntax
```AL
[Ok := ]  TextBuilder.AppendLine([Text: Text])
```
## Parameters
*TextBuilder*  
&emsp;Type: [TextBuilder](textbuilder-data-type.md)  
An instance of the [TextBuilder](textbuilder-data-type.md) data type.  

*[Optional] Text*  
&emsp;Type: [Text](../text/text-data-type.md)  
The string to append.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the copy of the specified string with the default line terminator succeeded, otherwise **false**. If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[TextBuilder Data Type](textbuilder-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)