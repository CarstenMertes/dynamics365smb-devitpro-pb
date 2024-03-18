---
title: "TextBuilder.EnsureCapacity(Integer) Method"
description: "Ensures that the capacity of this TextBuilder instance is at least the specified value."
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
# TextBuilder.EnsureCapacity(Integer) Method
> **Version**: _Available or changed with runtime version 1.0._

Ensures that the capacity of this TextBuilder instance is at least the specified value.


## Syntax
```AL
[Ok := ]  TextBuilder.EnsureCapacity(NewCapacity: Integer)
```
## Parameters
*TextBuilder*  
&emsp;Type: [TextBuilder](textbuilder-data-type.md)  
An instance of the [TextBuilder](textbuilder-data-type.md) data type.  

*NewCapacity*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The minimum capacity to ensure.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the capacity of the TextBuilder is at least the specified value, otherwise **false**. If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[TextBuilder Data Type](textbuilder-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)