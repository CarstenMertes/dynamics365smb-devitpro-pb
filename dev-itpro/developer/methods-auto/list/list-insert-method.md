---
title: "List.Insert(Integer, T) Method"
description: "Inserts an element into the List at the specified index."
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
# List.Insert(Integer, T) Method
> **Version**: _Available or changed with runtime version 1.0._

Inserts an element into the List at the specified index.


## Syntax
```AL
[Ok := ]  List.Insert(Index: Integer, Value: T)
```
## Parameters
*List*  
&emsp;Type: [List](list-data-type.md)  
An instance of the [List](list-data-type.md) data type.  

*Index*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The one-based index at which the value should be inserted.  

*Value*  
&emsp;Type: [T](list-data-type.md)  
The value to be inserted.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the index was within the valid range, otherwise **false**. If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

The type `T` is a dynamic type. When `List` is of type `Text` then `T` will change to `Text`. When `List` is of type `Integer`, then `T` will change to `Integer`.

## See Also
[List Data Type](list-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)