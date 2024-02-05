---
title: "System.CompressArray(Array of [Text]) Method"
description: "Moves all non-empty strings (text) in an array to the beginning of the array."
ms.author: solsen
ms.custom: na
ms.date: 03/24/2022
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# System.CompressArray(Array of [Text]) Method
> **Version**: _Available or changed with runtime version 1.0._

Moves all non-empty strings (text) in an array to the beginning of the array. The resulting StringArray has the same number of elements as the input array, but empty entries appear at the end of the array.


## Syntax
```AL
[Count := ]  System.CompressArray(StringArray: Array of [Text])
```
> [!NOTE]
> This method can be invoked without specifying the data type name.
## Parameters
*StringArray*  
&emsp;Type: [Text](../text/text-data-type.md)  
The string array that you want to compress.  


## Return Value
*[Optional] Count*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

When compressing an array of strings, the non-empty strings in the resulting array are sorted just like in the original array.  
  
The **CompressArray** method is useful for printing names and addresses. For instance, you can use this method to remove blank lines in account statements.  
  
This method compresses an array of Text or Code, but not BigText. The compression is performed by moving empty strings to the end of the array.  
  
For example, "Redmond", "Copenhagen", "", "Fargo", "Paris" is changed to "Redmond", "Copenhagen", "Fargo", "Paris", "".  
  
In [!INCLUDE[d365fin_long_md](../../includes/d365fin_long_md.md)], it is not supported to use the **CompressArray** method on multidimensional arrays. In earlier versions, **CompressArray** works for arrays of arrays.  
  
## Example

This example shows how to use the **CompressArray** method. The input array has the following values: Joe Raybon, One Meca Way, Atlanta.   

The output StringArray has the following values: Joe Raybon, One Meca Way, Atlanta.  
  
All non-empty entries have been moved to the beginning of the array.  
 
```al
var
    CustomerData: array[6] of Text;
begin
    CustomerData[1] := 'Joe Raybon';  
    CustomerData[2] := ''; // Empty string.  
    CustomerData[3] :='One Meca Way';  
    CustomerData[4] := '  '; // A non-empty string that contains blanks.  
    CustomerData[5] := 'Atlanta';  
    CustomerData[6] := ''; // Empty string.  
    Message('Before compression the address is: \%1\%2\%3\%4\%5\%6', CustomerData[1], CustomerData[2], CustomerData[3], CustomerData[4], CustomerData[5], CustomerData[6]);  
    CompressArray(CustomerData); // The empty lines (strings) are removed.  
    Message('After compression the address is: \%1\%2\%3\%4\%5\%6', CustomerData[1], CustomerData[2], CustomerData[3], CustomerData[4], CustomerData[5], CustomerData[6]);  
end;
```  
  
 The first message window displays the following:  
  
 **Before compression, the address is:**  
  
 **Joe Raybon**  
  
 **One Meca Way**  
  
 **Atlanta**  
  
 The second message window displays the following:  
  
 **After compression, the address is:**  
  
 **Joe Raybon**  
  
 **One Meca Way**  
  
 **Atlanta**  
  
 All empty strings, which cause blank lines, are moved to the end of the array.  
  
> [!NOTE]  
> Empty lines are not printed if they occur on the first or last line in a message window.  

## See Also

[System Data Type](system-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)