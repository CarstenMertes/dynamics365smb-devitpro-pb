---
title: "Text.Substring(Integer [, Integer]) Method"
description: "Retrieves a substring from this instance."
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
# Text.Substring(Integer [, Integer]) Method
> **Version**: _Available or changed with runtime version 1.0._

Retrieves a substring from this instance.


## Syntax
```AL
Substring :=   Text.Substring(StartIndex: Integer [, Count: Integer])
```
> [!NOTE]
> This method can be invoked without specifying the data type name.
## Parameters
*Text*  
&emsp;Type: [Text](text-data-type.md)  
An instance of the [Text](text-data-type.md) data type.  

*StartIndex*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The one-based starting character position of a substring in this instance.  

*[Optional] Count*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The number of characters in the substring.  


## Return Value
*Substring*  
&emsp;Type: [Text](text-data-type.md)  
The substring extracted from this instance.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[Text Data Type](text-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)