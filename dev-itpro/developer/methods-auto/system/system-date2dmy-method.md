---
title: "System.Date2DMY(Date, Integer) Method"
description: "Gets the day, month, or year of a Date Data Type."
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
# System.Date2DMY(Date, Integer) Method
> **Version**: _Available or changed with runtime version 1.0._

Gets the day, month, or year of a Date Data Type.


## Syntax
```AL
Number :=   System.Date2DMY(Date: Date, Value: Integer)
```
> [!NOTE]
> This method can be invoked without specifying the data type name.
## Parameters
*Date*  
&emsp;Type: [Date](../date/date-data-type.md)  
The input date.  

*Value*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
Specifies what the method should return. The valid options are 1, 2, and 3.
- The value 1 corresponds to Day (1-31).
- The value 2 corresponds to Month (1-12).
- The value 3 corresponds to Year.  


## Return Value
*Number*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)


## Example

This example shows how to use the **Date2DMY** method.
 
```al
var
    InputDate: Date;
    Day: Integer;
    Month: Integer;
    Year: Integer;
    Text000: Label 'Today is day %1 of month %2 of the year %3.';
begin
    InputDate := Today;  
    Day := Date2DMY(InputDate,1);  
    Month := Date2DMY(InputDate,2);  
    Year := Date2DMY(InputDate,3);  
    Message(Text000,Day,Month,Year); 
end; 
```  
  
The message window displays the following:  
  
**Today is day 16 of month 2 of the year 2014.**  
 
## See Also

[System Data Type](system-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)