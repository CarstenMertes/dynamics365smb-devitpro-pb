---
title: "System.Sleep(Integer) Method"
description: "Returns control to the operating system for a specified time."
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
# System.Sleep(Integer) Method
> **Version**: _Available or changed with runtime version 1.0._

Returns control to the operating system for a specified time.


## Syntax
```AL
 System.Sleep(Duration: Integer)
```
> [!NOTE]
> This method can be invoked without specifying the data type name.
## Parameters
*Duration*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The number of milliseconds to return control to the operating system.  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

When you use the Sleep method, control is guaranteed to return to the operating system for at least *Duration* milliseconds.  
  
> [!NOTE]  
> The period may be longer than *Duration* milliseconds, depending on what the operating system is doing at the time that control is to return to the caller.  
  
  
## See Also

[System Data Type](system-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)