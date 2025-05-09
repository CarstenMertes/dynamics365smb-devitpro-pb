---
title: "Label.Substring(Integer [, Integer]) Method"
description: "Retrieves a substring from this instance."
ms.author: solsen
ms.date: 02/18/2025
ms.topic: reference
author: SusanneWindfeldPedersen
ms.reviewer: solsen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Label.Substring(Integer [, Integer]) Method
> **Version**: _Available or changed with runtime version 15.0._

Retrieves a substring from this instance.


## Syntax
```AL
Substring :=   Label.Substring(StartIndex: Integer [, Count: Integer])
```
## Parameters
*Label*  
&emsp;Type: [Label](label-data-type.md)  
An instance of the [Label](label-data-type.md) data type.  

*StartIndex*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The one-based starting character position of a substring in this instance.  

*[Optional] Count*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The number of characters in the substring.  


## Return Value
*Substring*  
&emsp;Type: [Text](../text/text-data-type.md)  
The substring extracted from this instance.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## Related information
[Label data type](label-data-type.md)  
[Getting started with AL](../../devenv-get-started.md)  
[Developing extensions](../../devenv-dev-overview.md)