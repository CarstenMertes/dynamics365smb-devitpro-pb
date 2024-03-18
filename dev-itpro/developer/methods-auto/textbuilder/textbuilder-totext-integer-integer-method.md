---
title: "TextBuilder.ToText(Integer, Integer) Method"
description: "Converts the value of a substring of this TextBuilder instance to a Text."
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
# TextBuilder.ToText(Integer, Integer) Method
> **Version**: _Available or changed with runtime version 1.0._

Converts the value of a substring of this TextBuilder instance to a Text.


## Syntax
```AL
Result :=   TextBuilder.ToText(StartIndex: Integer, Count: Integer)
```
## Parameters
*TextBuilder*  
&emsp;Type: [TextBuilder](textbuilder-data-type.md)  
An instance of the [TextBuilder](textbuilder-data-type.md) data type.  

*StartIndex*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The starting position of the substring in this TextBuilder instance.  

*Count*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The number of characters in the substring.  


## Return Value
*Result*  
&emsp;Type: [Text](../text/text-data-type.md)  
The result text substring.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[TextBuilder Data Type](textbuilder-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)