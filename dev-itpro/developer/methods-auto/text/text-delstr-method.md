---
title: "Text.DelStr(Text, Integer [, Integer]) Method"
description: "Deletes a substring inside a string (text or code)."
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
# Text.DelStr(Text, Integer [, Integer]) Method
> **Version**: _Available or changed with runtime version 1.0._

Deletes a substring inside a string (text or code).


## Syntax
```AL
NewString :=   Text.DelStr(String: Text, Position: Integer [, Length: Integer])
```
> [!NOTE]
> This method can be invoked without specifying the data type name.
## Parameters
*String*  
&emsp;Type: [Text](text-data-type.md)  
The input string.  

*Position*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The position of the first character that you want to delete. Position must be greater than zero (0). If Position exceeds the length of String, DELSTR returns the original string, unchanged.  

*[Optional] Length*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
Specifies how many characters to delete. Length must be greater than zero (0).  


## Return Value
*NewString*  
&emsp;Type: [Text](text-data-type.md)  
The input string without the specified substring.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  
 If you omit *Length*, all the characters starting with *Position* are deleted until the end of the string.  
  
 If you omit *Length* and *Position* is less than 1, then an error is returned.  
  
 If you omit *Length* and *Position* is greater than the length of *String*, then *String* is returned unchanged.  
  
## Example

```al
var
    Str: Text[40];
    NewStr: Text[40];
    Position: Integer;
    Length: Integer;
    Text000: TexConst ENU='Adjusting prices - Please wait.';
    Text001: TexConst ENU='The original string:>%1<';
    Text002: TexConst ENU='The original modified:>%2<';
begin
    Str := Text000;  
    Position := 11; // Remove the word 'prices' and a blank.  
    Length := 7;  
    NewStr := DelStr(Str, Position, Length);  
    Message(Text001, Str);  
    Message(Text002, NewStr);  
end;
```  
  
 The first message window displays the following:  
  
 **The original string:**  
  
 **>Adjusting prices - Please wait.\<**  
  
 The second message window displays the following:  
  
 **The modified string:**  
  
 **>Adjusting - Please wait.\<**  
  

## See Also
[Text Data Type](text-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)