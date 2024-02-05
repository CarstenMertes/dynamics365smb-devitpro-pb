---
title: "Session.GetModuleExecutionContext([Guid]) Method"
description: "Gets the current session's execution context scoped to a specific module."
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
# Session.GetModuleExecutionContext([Guid]) Method
> **Version**: _Available or changed with runtime version 1.0._

Gets the current session's execution context scoped to a specific module.


## Syntax
```AL
ExecutionContext :=   Session.GetModuleExecutionContext([AppId: Guid])
```
> [!NOTE]
> This method can be invoked without specifying the data type name.
## Parameters
*[Optional] AppId*  
&emsp;Type: [Guid](../guid/guid-data-type.md)  
The application ID.  


## Return Value
*ExecutionContext*  
&emsp;Type: [ExecutionContext](../executioncontext/executioncontext-option.md)  
The current session's execution context scoped to a specific module.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[Session Data Type](session-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)