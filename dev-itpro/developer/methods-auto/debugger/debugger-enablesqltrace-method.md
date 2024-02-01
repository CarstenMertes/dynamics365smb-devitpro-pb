---
title: "Debugger.EnableSqlTrace(Integer [, Boolean]) Method"
description: "Enables or verifies SQL tracing."
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
# Debugger.EnableSqlTrace(Integer [, Boolean]) Method
> **Version**: _Available or changed with runtime version 1.0._

Enables or verifies SQL tracing. If you enable SQL tracing, then SQL Server events for selected sessions on the server instance are collected.


## Syntax
```AL
[IsEnabled := ]  Debugger.EnableSqlTrace(SessionID: Integer [, NewIsEnabled: Boolean])
```
## Parameters
*SessionID*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The ID of the session for which you want to enable the SQL trace, or for which you want to verify if tracing is enabled.If you specify 0 and you specify the NewIsEnabled parameter, then tracing is enabled for all existing sessions and all new sessions on the current server instance. If you specify 0 and you omit the NewIsEnabled parameter, then the function returns true if tracing is enabled for new sessions on the current server instance. If the session ID that you specify does not exist and you specify the NewIsEnabled parameter, then a run-time error occurs. If the session ID that you specify does not exist and you do not specify the NewIsEnabled parameter, then the function returns false.  

*[Optional] NewIsEnabled*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
If you specify the optional NewIsEnabled parameter, then the method sets whether tracing is enabled. true if you want to enable tracing for the specified session; false if you want to disable tracing. If you omit the NewIsEnabled parameter, then the function verifies if tracing is enabled.  


## Return Value
*[Optional] IsEnabled*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

You use Microsoft SQL Server Profiler to view traces. For more information, see [Using SQL Server Profiler](/previous-versions/sql/sql-server-2008-r2/ms187929(v=sql.105)). To start SQL Server Profiler, in **SQL Server Management Studio**, on the **Tools** menu, choose **SQL Server Profiler**.  
  
You can also enable and disable SQL tracing by using the **Start Full SQL Tracing** and **Stop Full SQL Tracing** buttons on the **Session List** page.  

## See Also
[Debugger Data Type](debugger-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)