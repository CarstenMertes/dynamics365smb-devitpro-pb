---
title: "TextBuilder.Remove(Integer, Integer) Method"
description: "Removes the specified range of characters from this TextBuilder instance."
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
# TextBuilder.Remove(Integer, Integer) Method
> **Version**: _Available or changed with runtime version 1.0._

Removes the specified range of characters from this TextBuilder instance.


## Syntax
```AL
[Ok := ]  TextBuilder.Remove(StartIndex: Integer, Count: Integer)
```
## Parameters
*TextBuilder*  
&emsp;Type: [TextBuilder](textbuilder-data-type.md)  
An instance of the [TextBuilder](textbuilder-data-type.md) data type.  

*StartIndex*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The one-based position in this TextBuilder instance where removal begins.  

*Count*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The number of characters to remove.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the specified range of characters was successfully removed, otherwise **false**. If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[TextBuilder Data Type](textbuilder-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)