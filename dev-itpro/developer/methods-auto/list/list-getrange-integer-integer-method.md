---
title: "List.GetRange(Integer, Integer) Method"
description: "Get a shallow copy of a range of elements in the source."
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
# List.GetRange(Integer, Integer) Method
> **Version**: _Available or changed with runtime version 1.0._

Get a shallow copy of a range of elements in the source.


## Syntax
```AL
Result :=   List.GetRange(Index: Integer, Count: Integer)
```
## Parameters
*List*  
&emsp;Type: [List](list-data-type.md)  
An instance of the [List](list-data-type.md) data type.  

*Index*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The one-based List index at which the range starts.  

*Count*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The number of elements in the range.  


## Return Value
*Result*  
&emsp;Type: [List of [T]](list-data-type.md)  
A shallow copy of a range of elements in the source List.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

The type `T` is a dynamic type. When `List` is of type `Text` then `T` will change to `Text`. When `List` is of type `Integer`, then `T` will change to `Integer`.

For examples on *shallow copy* versus *deep copy*, see [List Data Type](list-data-type.md).

## See Also
[List Data Type](list-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)