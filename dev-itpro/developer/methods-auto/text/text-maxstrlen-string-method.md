---
title: "Text.MaxStrLen(Text) Method"
description: "Gets the maximum defined length of a string variable."
ms.author: solsen
ms.custom: na
ms.date: 12/06/2022
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Text.MaxStrLen(Text) Method
> **Version**: _Available or changed with runtime version 1.0._

Gets the maximum defined length of a string variable.


## Syntax
```AL
MaxLength :=   Text.MaxStrLen(String: Text)
```
> [!NOTE]
> This method can be invoked without specifying the data type name.
## Parameters
*String*  
&emsp;Type: [Text](text-data-type.md)  
The string variable for which you want to find the maximum length.  


## Return Value
*MaxLength*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The maximum length of the string variable.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  
 If you call this method on a Variant, it returns an error.  
  
## Example

```al
var
    City: Text[30];
    MaxLength: Integer;
    Length: Integer;
    Text000: Label 'Vedbaek';
    Text001: Label 'The MaxStrLen method returns %1,\\';
    Text002: Label 'whereas the StrLen method returns %2';
begin
    City := Text000;  
    MaxLength := MaxStrLen(City);  
    Length := StrLen(City);  
    Message(Text001 + Text002, MaxLength, Length);  
end;
```  
  
 The message window displays the following:  
  
 **The MaxStrLen method returns 30,**  
  
 **whereas the StrLen method returns 7.**  
  

## See Also
[Text Data Type](text-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)