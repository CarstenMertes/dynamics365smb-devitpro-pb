---
title: "TextBuilder.Replace(Text, Text, Integer, Integer) Method"
description: "Replaces, within a substring of this instance, all occurrences of a specified string in this TextBuilder instance with another specified string."
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
# TextBuilder.Replace(Text, Text, Integer, Integer) Method
> **Version**: _Available or changed with runtime version 1.0._

Replaces, within a substring of this instance, all occurrences of a specified string in this TextBuilder instance with another specified string.


## Syntax
```AL
[Ok := ]  TextBuilder.Replace(OldText: Text, NewText: Text, StartIndex: Integer, Count: Integer)
```
## Parameters
*TextBuilder*  
&emsp;Type: [TextBuilder](textbuilder-data-type.md)  
An instance of the [TextBuilder](textbuilder-data-type.md) data type.  

*OldText*  
&emsp;Type: [Text](../text/text-data-type.md)  
The string to replace.  

*NewText*  
&emsp;Type: [Text](../text/text-data-type.md)  
The string that replaces OldText.  

*StartIndex*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The position in this TextBuilder instance where the substring begins.  

*Count*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The length of the substring.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if all occurrences of a specified string were successfully replaced, otherwise **false**. If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[TextBuilder Data Type](textbuilder-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)