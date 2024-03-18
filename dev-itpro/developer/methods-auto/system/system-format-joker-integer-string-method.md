---
title: "System.Format(Any, Integer, Text) Method"
description: "Formats a value into a string."
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
# System.Format(Any, Integer, Text) Method
> **Version**: _Available or changed with runtime version 1.0._

Formats a value into a string.


## Syntax
```AL
String :=   System.Format(Value: Any, Length: Integer, FormatString: Text)
```
> [!NOTE]
> This method can be invoked without specifying the data type name.
## Parameters
*Value*  
&emsp;Type: [Any](../any/any-data-type.md)  
This is an AL variable (expression) of any simple data type, such as Option, Integer, BigInteger, Decimal, Char, Text, Code, Date, Time, DateTime, Boolean, or GUID. If, when the system formats Value, the result is a value larger than the maximum length MAXSTRLEN method (Code, Text) of String, a run-time error occurs.  

*Length*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
This optional parameter specifies the length of String.  

*FormatString*  
&emsp;Type: [Text](../text/text-data-type.md)  
A literal string that defines a format as in the Format Property.  


## Return Value
*String*  
&emsp;Type: [Text](../text/text-data-type.md)  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

For the *Length* parameter, the following rules apply:  

- If *Length* = 0 then the entire value is returned (default).  

- If *Length* > 0 then the returned string will be exactly *Length* characters.  

   If *Value* is less than *Length* characters, then either leading or trailing spaces are inserted, depending on the format that you select.  

   If *Value* exceeds *Length* characters, then *String* is truncated to *Length* characters.  

- If *Length* < 0 then the returned string will not have leading or trailing spaces.  

   If *Value* is less than *Length* characters, the length of *String* will equal the length of *Value*.  

   If *Value* exceeds *Length* characters, then *String* is truncated to *Length* characters.

For more information, see [Formatting Values, Dates, and Time](../../devenv-format-property.md).

## Example 1

```al
var
    Text000: Label 'The formatted value >%1<';
begin
    Message(Text000, Format(-123456.78, 12, 3));  
    Message(Text000, Format(-123456.78, 12, '<Standard Format,3>'));  
    Message(Text000, Format(-123456.78, 12, '<Integer Thousand><Decimals><Sign,1>'));  
end;

```  

The Regional and Language settings on the computer on which you run the code affect how the string is displayed. For example, on a computer that has the regional format set to English (United States), the message window displays the following:  

**The formatted value: > 123,456.78-\<**  
**The formatted value: > 123,456.78-\<**  
**The formatted value: > 123,456.78-\<**  

On a computer that has the regional format set to Danish \(Denmark\), the message window displays the following:  

**The formatted value: > 123.456,78-\<**  
**The formatted value: > 123.456,78-\<**  
**The formatted value: > 123.456,78-\<**  

## Example 2

This example shows how to use a string to build a format.

```al
var
    Text000: Label 'Today is %1';
begin 
    Message(Text000, Format(Today,0,'<Month Text> <Day>'));  
end;
```  

The message window displays the following:  

**Today is April 15.**  

## See Also

[Formatting Values, Dates, and Time](../../devenv-format-property.md)  
[System Data Type](system-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)
