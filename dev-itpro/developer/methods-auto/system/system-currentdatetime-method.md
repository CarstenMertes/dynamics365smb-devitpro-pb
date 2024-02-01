---
title: "System.CurrentDateTime() Method"
description: "Gets the current DateTime."
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
# System.CurrentDateTime() Method
> **Version**: _Available or changed with runtime version 1.0._

Gets the current DateTime.


## Syntax
```AL
Datetime :=   System.CurrentDateTime()
```
> [!NOTE]
> This method can be invoked using property access syntax.
> [!NOTE]
> This method can be invoked without specifying the data type name.


## Return Value
*Datetime*  
&emsp;Type: [DateTime](../datetime/datetime-data-type.md)  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Example

```al
var
    TestDateTime : DateTime;

TestDateTime := CurrentDateTime;  
Message(Format(TestDateTime));  
```  
  
The message window displays the current date and time.
 
## See Also
[System Data Type](system-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)