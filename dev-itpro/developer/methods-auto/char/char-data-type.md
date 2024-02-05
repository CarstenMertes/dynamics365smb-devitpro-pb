---
title: "Char Data Type"
description: "Stores a single, 16-bit character as a value in the range 0 to 65535."
ms.author: solsen
ms.custom: na
ms.date: 06/23/2021
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Char Data Type
> **Version**: _Available or changed with runtime version 1.0._

Stores a single, 16-bit character as a value in the range 0 to 65535. You can convert this data type from a number to a character and vice versa. This means you can use mathematical operators on Char variables.




[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Example

The following example assumes that you have a Char variable named C and a Text or Code variable named S.  
  
You can assign a constant string of the length 1 to a Char variable, as shown in the first line of the following code example. You can assign a single Char in a Text or Code variable to a Char variable, as shown in the second line of the following code example. You can assign a numeric value to a Char variable, as shown in the third line of the following code example.  

 <!-- //NAV 
 A Char variable represents Unicode characters in the same way as the .NET Framework Char structure. For more information about the .NET Framework Char structure, see [Char Structure](/dotnet/api/system.char).  --> 
  
```al
C := 'A';  
C := S[2];  
C := 65;  
```  
  
You cannot assign a Char to a position greater than the position of the null terminator. For example, if the value of the Text variable *MyText* is 'abc', then the null terminator is at position 4 and the following assignment causes a run-time error to occur.  
  
```al
MyText[5] := 'e';  
```  
  
## See Also

[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)