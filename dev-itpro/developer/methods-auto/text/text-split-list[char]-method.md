---
title: "Text.Split(List of [Char]) Method"
description: "Splits a string into a maximum number of substrings based on a collection of separators."
ms.author: solsen
ms.custom: na
ms.date: 12/06/2022
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Text.Split(List of [Char]) Method
> **Version**: _Available or changed with runtime version 1.0._

Splits a string into a maximum number of substrings based on a collection of separators.


## Syntax
```AL
Result :=   Text.Split(Separators: List of [Char])
```
> [!NOTE]
> This method can be invoked without specifying the data type name.
## Parameters
*Text*  
&emsp;Type: [Text](text-data-type.md)  
An instance of the [Text](text-data-type.md) data type.  

*Separators*  
&emsp;Type: [List of [Char]](../list/list-data-type.md)  
A collection of separators that delimit the substrings in this string.  


## Return Value
*Result*  
&emsp;Type: [List of [Text]](../list/list-data-type.md)  
The collection of substrings from the original string based on the collection of separators.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[Text Data Type](text-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)