---
title: "List.Contains(T) Method"
description: "Determines whether an element is in the List."
ms.author: solsen
ms.custom: na
ms.date: 01/10/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# List.Contains(T) Method
> **Version**: _Available or changed with runtime version 1.0._

Determines whether an element is in the List.


## Syntax
```AL
Result :=   List.Contains(Value: T)
```
## Parameters
*List*  
&emsp;Type: [List](list-data-type.md)  
An instance of the [List](list-data-type.md) data type.  

*Value*  
&emsp;Type: [T](list-data-type.md)  
The value to locate in the List.  


## Return Value
*Result*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the List contains the value, otherwise **false**.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

The type `T` is a dynamic type. When `List` is of type `Text` then `T` will change to `Text`. When `List` is of type `Integer`, then `T` will change to `Integer`.

## See Also
[List Data Type](list-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)