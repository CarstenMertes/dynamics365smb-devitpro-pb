---
title: "Text.ConvertStr(Text, Text, Text) Method"
description: "Replaces all chars in source found in FromCharacters with the corresponding char in ToCharacters and returns the converted string."
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
# Text.ConvertStr(Text, Text, Text) Method
> **Version**: _Available or changed with runtime version 1.0._

Replaces all chars in source found in FromCharacters with the corresponding char in ToCharacters and returns the converted string. If the length of the FromCharacters parameter and the ToChars parameter are different, an exception is thrown. If the parameter FromCharacters or the parameter ToChars is empty, the source is returned unmodified. Each element in source is only converted ONCE a double-replacement cannot happen.


## Syntax
```AL
NewString :=   Text.ConvertStr(String: Text, FromCharacters: Text, ToCharacters: Text)
```
> [!NOTE]
> This method can be invoked without specifying the data type name.
## Parameters
*String*  
&emsp;Type: [Text](text-data-type.md)  
The string that you want to convert.  

*FromCharacters*  
&emsp;Type: [Text](text-data-type.md)  
The characters that you want to replace. This function is case-sensitive.  

*ToCharacters*  
&emsp;Type: [Text](text-data-type.md)  
The new characters with which you want to replace the FromCharacters. This function is case-sensitive.  


## Return Value
*NewString*  
&emsp;Type: [Text](text-data-type.md)  
The input string with the converted characters.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  
 The characters in the *FromCharacters* parameter are replaced by the characters in the *ToCharacters* parameter.  
  
 If the lengths of the *FromCharacters* and *ToCharacters* strings are not equal, then a run-time error occurs.  
  
 If either the *FromCharacters* or the *ToCharacters* strings are empty, then the source is returned unchanged.  
  
## Example  

```al
var
    OriginalString: Text[30];
    FromChars: Text[30];
    ToChars: Text[30];
    NewString: Text[30];
    Text000: Label 'Do you want to leave without saving?';
    Text001: Label 'lws';
    Text002: Label 'LWS';
    Text003: Label 'The original sentence is\\: %1';
    Text004: Label 'The sentence is converted to:\\ %1';
begin
    OriginalString := Text000;  
    FromChars := Text001;  
    ToChars := Text002;   
    NewString := ConvertStr(OriginalString, FromChars, ToChars);  
    Message(Text003, OriginalString);  
    Message(Text004, NewString);  
end;
```  
  
 The first message window shows:  
  
 **The original sentence is:**  
  
 **Do you want to leave without saving?**  
  
 The second message window shows:  
  
 **The sentence is converted to:**  
  
 **Do you Want to Leave Without Saving?**  
  

## See Also
[Text Data Type](text-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)