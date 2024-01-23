---
title: "Database.SerialNumber() Method"
description: "Gets a string that contains the serial number of the license file for your system."
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
# Database.SerialNumber() Method
> **Version**: _Available or changed with runtime version 1.0._

Gets a string that contains the serial number of the license file for your system.


## Syntax
```AL
String :=   Database.SerialNumber()
```
> [!NOTE]
> This method can be invoked using property access syntax.
> [!NOTE]
> This method can be invoked without specifying the data type name.

## Return Value
*String*  
&emsp;Type: [Text](../text/text-data-type.md)  
The serial number.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Example

```al
var
    SN: Text[30];
    Text000: Label 'The serial number for this software package is:%1.';
begin 
    SN := SerialNumber;  
    Message(Text000, SN);  
end;
```  
  
The output of this example is as follows:  
  
**The serial number for this software package is:**  
  
**W1-ZA-002-6R75A-7**
  
> [!NOTE]  
> The serial number depends on your licensed version of [!INCLUDE[d365fin_md](../../includes/d365fin_md.md)]. The serial number shown here is an example.

## See Also
[Database Data Type](database-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)