---
title: "Array methods"
description: "Methods of the type array in AL for Business Central"
ms.custom: na
ms.date: 04/20/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---

# Array methods

An array is a data structure that contains many variables, which are accessed through computed indices. An index is the location of the variable stored in an array. The variables contained in an array are also called the elements of the array. The array always stores elements of the same data type.

An array has a rank that determines the number of indices that is how long it takes to reach an element. And if there are repeating elements, their rank is same as their first occurrence in the array. The rank of an array is also referred to as the dimension of the array. An array with a rank of one is called a single-dimensional array. An array with a rank greater than one is called a multi-dimensional array. Specific sized multi-dimensional arrays are often referred to as two-dimensional arrays, three-dimensional arrays, and so on. Each dimension of an array has an associated length, which is an integral number greater than or equal to zero. The maximum number of dimensions is 10 and the total number of elements in all dimensions is 1,000,000.

The length of a dimension determines the valid range of indices for that dimension. For a dimension of length N, indices can range from **1 to N** inclusive. The total number of elements in an array is the product of the lengths of each dimension in the array. If one or more of the dimensions of an array have a length of zero, the array is considered to be empty.

## Syntax 

The syntax for declaring an array of a specific type is the following:

```AL
array [Dimension] of Type;
```

The `Dimension` is a comma-delimited list of integer literals greater than 0, where each integer defines the number of elements in that dimension. 

The `Type` is the element type of the array.

## Code example 

The following code sample shows the declaration of an array with a simple element type.

```AL
arrayOfInteger: array [10] of Integer;
```

The following code sample shows the declaration of an array with an element type of a fixed length.

```AL
arrayOfCode: array [10] of Code[20];
arrayOfText: array [10] of Text[20];
```

The following code sample shows the declaration of an array with a complex element type.

```AL
arrayOfCodeunits: array [10] of Codeunit 10;
arrayOfQueryes: array [10] of Query "My Query";
arrayOfTemporaryRecords: array [10] of Record 10 Temporary;
arrayOfDotNetVariables: array [10] of DotNet String;
```

## Methods

The following AL methods for arrays are available:  

[ArrayLen Method](../methods-auto/system/system-arraylen-method.md)  
[CompressArray Method](../methods-auto/system/system-compressarray-method.md)  
[CopyArray Method](../methods-auto/system/system-copyarray-method.md)

## Array of temporary records

The following code sample shows the declaration of an array of temporary Item records:

```AL
itemRecArrayTemp: array[2] of Record Item temporary;
```

In this case, each element of the array contains a temporary Item record referencing the same temporary table, meaning that an insert into `itemRecArrayTemp[0]` is also reflected in `itemRecArrayTemp[1]`.

This is the same behavior as using [Copy(RecordRef [, Boolean])](../methods-auto/recordref/recordref-copy-recordref-boolean-method.md) with the `ShareTable` parameter set to `true`.

## See Also  

[AL Method Reference](../methods-auto/library.md)  
