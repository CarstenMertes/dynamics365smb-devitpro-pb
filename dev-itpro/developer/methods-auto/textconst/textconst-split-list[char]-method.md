---
title: "TextConst.Split(List of [Char]) Method"
description: "Splits a string into a maximum number of substrings based on a collection of separators."
ms.author: solsen
ms.date: 08/08/2025
ms.topic: reference
author: SusanneWindfeldPedersen
ms.reviewer: solsen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# TextConst.Split(List of [Char]) Method
> **Version**: _Available or changed with runtime version 15.1._

Splits a string into a maximum number of substrings based on a collection of separators.


## Syntax
```AL
Result :=   TextConst.Split(Separators: List of [Char])
```
## Parameters
*TextConst*  
&emsp;Type: [TextConst](textconst-data-type.md)  
An instance of the [TextConst](textconst-data-type.md) data type.  

*Separators*  
&emsp;Type: [List of [Char]](../list/list-data-type.md)  
A collection of separators that delimit the substrings in this string.  


## Return Value
*Result*  
&emsp;Type: [List of [Text]](../list/list-data-type.md)  
The collection of substrings from the original string based on the collection of separators.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[TextConst data type](textconst-data-type.md)  
[Getting started with AL](../../devenv-get-started.md)  
[Developing extensions](../../devenv-dev-overview.md)