---
title: "Debugger.BreakOnRecordChanges(Boolean) Method"
description: "Breaks execution before a change to a record occurs."
ms.author: solsen
ms.date: 08/26/2024
ms.topic: reference
author: SusanneWindfeldPedersen
ms.reviewer: solsen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Debugger.BreakOnRecordChanges(Boolean) Method
> **Version**: _Available or changed with runtime version 1.0 until version 4.0 where it was deprecated._

Breaks execution before a change to a record occurs.


## Syntax
```AL
[Ok := ]  Debugger.BreakOnRecordChanges(Ok: Boolean)
```
## Parameters
*Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
Specifies whether the debugger should break execution when a change to a record occurs. If Ok is true, then the debugger breaks before creating, updating, or deleting a record.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the operation was successful; otherwise **false**.   If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

If you omit this optional return value and if the break is not set successfully, then a run-time error occurs. If you include the return value, then you must handle any errors.

## Related information
[Debugger Data Type](debugger-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)