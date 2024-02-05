---
title: "System.Random(Integer) Method"
description: "Returns a pseudo-random number."
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
# System.Random(Integer) Method
> **Version**: _Available or changed with runtime version 1.0._

Returns a pseudo-random number.


## Syntax
```AL
Number :=   System.Random(MaxNumber: Integer)
```
> [!NOTE]
> This method can be invoked without specifying the data type name.
## Parameters
*MaxNumber*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The largest acceptable number. In effect, you are setting a range from one (1) to the number that you specify with the MaxNumber parameter.  


## Return Value
*Number*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

If *MaxNumber* is negative it acts as a positive.  
  
If *MaxNumber* is zero, this method always returns 1.  
  
A number is always chosen from the same set of numbers. Use [Randomize Method)](../system/system-randomize-method.md) to generate a new set of numbers.  
  
## Example

This example shows how to generate a pseudo-random number. The value of the variable Number2 is positive though the value of *MaxNumber* is negative and the value of the variable Number3 is always 1 because *MaxNumber* is 0.  
  
```al
var
    x: Integer;
    y: Integer;
    z: Integer;
    Number1: Integer;
    Number2: Integer;
    Number3: Integer;
    Text000: Label 'Number1 = %1, Number2 = %2, Number3 = %3';
begin
    x := 100; // x is assigned a positive value.  
    y := -100; // y is assigned a negative value.  
    z := 0; // z is assigned zero.  
    Number1 := Random(x);  
    Number2 := Random(y);  
    Number3 := Random(z);  
    Message(Text000, Number1, Number2, Number3);  
end;
```  

## See Also

[System Data Type](system-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)