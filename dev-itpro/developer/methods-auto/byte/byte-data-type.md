---
title: "Byte data type"
description: "Stores a single, 8-bit character as a value in the range 0 to 255."
ms.author: solsen
ms.date: 08/08/2025
ms.topic: reference
author: SusanneWindfeldPedersen
ms.reviewer: solsen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Byte data type
> **Version**: _Available or changed with runtime version 1.0._

Stores a single, 8-bit character as a value in the range 0 to 255. You can easily convert this data type from a number to a character and vice versa. This means you can use mathematical operators on Byte variables.



## Instance methods
The following methods are available on instances of the Byte data type.

|Method name|Description|
|-----------|-----------|
|[ToText()](byte-totext-method.md)|Converts the value to a text. Equivalent to calling Format(value, 0, 0).|
|[ToText([Boolean])](byte-totext-boolean-method.md)|Converts the value to a text. Equivalent to calling Format(value, 0, 0).|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Example

The following example assumes that you have a Byte variable named B and a Text variable named S.  
  
You can assign a constant string of the length 1 to a Byte variable, as shown in the first line of the following code example. You can assign a single character in a Text or Code variable to a Byte variable, as shown in the second line of the following code example. You can assign a numeric value to a Byte variable, as shown in the third line of the following code example. This causes the Byte variable to contain the character from the ASCII character set that corresponds to the numeric ASCII code.  
  
```al
B := 'A';  
B := S[2];  
B := 65;  
```  
  
You cannot assign a character to a position greater than the position of the null terminator. For example, if the value of the text variable *MyText* is 'abc', then the null terminator is at position 4 and the following assignment causes a run-time error to occur.  
  
```al
MyText[5] := 'e';  
```  
  
## Related information

[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  