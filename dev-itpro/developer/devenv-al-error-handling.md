---
title: "AL error handling"
description: Deal with unexpected situations that occur when code is run in AL for Business Central
ms.custom: na
ms.date: 12/21/2023
ms.reviewer: na
ms.topic: conceptual
author: SusanneWindfeldPedersen
ms.collection: get-started
---

# AL error handling

[!INCLUDE [getstarted-contributions](includes/getstarted-contributions.md)]

The AL language has many error handling features, which can help you deal with unexpected situations that occur when code is run. This section contains articles about using these methods in AL to handle errors that occur during code execution, while making sure that your application has a consistent user interface. 

The following articles discuss the different aspects of error handling in AL:

- [Failure modeling and robust coding practices](devenv-robust-coding-practices.md)  
- [Understanding the error dialog](devenv-error-dialog.md)   
- [User experience guidelines for errors](devenv-error-handling-guidelines.md)  
- [Actionable errors](devenv-actionable-errors.md) 
- [Collecting errors](devenv-error-collection.md) 
- [Handling errors using Try methods](devenv-handling-errors-using-try-methods.md)   
- [Understanding the error dialog](devenv-error-dialog.md)   

## Error handling methods in AL

For examples of using different error handling methods in AL, see the following table:

| Method | Description |
|--------|---------|
|[ClearLastError Method](methods-auto/system/system-clearlasterror-method.md)| Removes the last error message from memory. |
|[Dialog Data Type](methods-auto/dialog/dialog-data-type.md)| Represents a dialog window. |
|[Error Method](methods-auto/dialog/dialog-error-errorinfo-method.md) | Displays an error message and ends the execution of AL code.|
|[ErrorInfo Data Type](methods-auto/errorinfo/errorinfo-data-type.md) | Contains a set of methods that helps identify errors, classify these errors, send errors to telemetry and display UI messages. Go to the data type article for an overview.|
|[System Data Type](methods-auto/system/system-data-type.md)|Is a complex data type and contains multiple methods for getting and classifying errors.|
|[GetLastErrorCallStack Method](methods-auto/system/system-getlasterrorcallstack-method.md)| Gets the call stack from where the last error occurred. |
|[GetLastErrorCode Method](methods-auto/system/system-getlasterrorcode-method.md)| Gets the classification of the last error that occurred. |
|[GetLastErrorObject Method](methods-auto/system/system-getlasterrorobject-method.md)| Gets the last System.Exception object that occurred. |
|[GetLastErrorText Method](methods-auto/system/system-getlasterrortext--method.md)| Gets the last error that occurred in the debugger. |

> [!TIP]  
> If you already know the name of a data type, use the **Filter by title** field in the upper left corner, above the table of contents to find the topic faster.

## Error handling strategies

For examples of different error handling strategies, see the following table:

| If you want to...| Then use|
|------------------|---------|
| Run a code unit and decide to do something if an error occurs. | `if not Codeunit.run()`. For more information, see [Codeunit.Run return value](methods-auto/codeunit/codeunit-run-method.md) |
| Check for an error and show an error dialog to the user. |`Dialog.Error(Message: ErrorInfo)`. For more information, see [Error Method](methods-auto/dialog/dialog-error-errorinfo-method.md). |
| Check for an error and show an error dialog to the user with added support information. | [Using the ErrorInfo Data Type with the Error Method](methods-auto/errorinfo/errorinfo-data-type.md) |
| Do bulk validations in AL and not show an error dialog for each of them to the user. | [Collecting Errors](devenv-error-collection.md) |
| Catch errors raised by other AL methods| [Handling Errors using Try Methods](devenv-handling-errors-using-try-methods.md) | 
| Catch errors/exceptions that are thrown during .NET framework interoperability operations (on-premises only). | [Handling .NET Exceptions using Try Methods](devenv-handling-errors-using-try-methods.md)|
| Handle errors happening in Page Background Tasks | The `OnPageBackgroundTaskError` trigger of the page. For more information, see [Handling errors (in Page Background Tasks)](devenv-page-background-tasks.md#handling-errors). | 
| Log an error that happens within a database transaction (that rollback) | Either log the error in a new session using a background session, or log the error to telemetry (see [LogMessage](./methods-auto/session/session-logmessage-string-string-verbosity-dataclassification-telemetryscope-dictionary[text,text]-method.md) or [Telemetry.LogError](../administration/telemetry-feature-telemetry.md#LogError) ). | 


## Guidelines for error messages

Improving error handling and error messages reduces friction for the users and highly impacts the user experience. Clear, informative error messages help users understand what went wrong and how to correct it, reducing frustration, and improving user satisfaction. 

For guidance on how to formulate good error messages, see [Error message best practices - what to say?](devenv-error-handling-guidelines.md#error_message_best_practices).


## Error telemetry (emitted by the AL runtime)

When a user gets an error dialog while working in [!INCLUDE[prod_short](../includes/prod_short.md)], a telemetry signal is emitted, which can be logged in an [!INCLUDE[appInsights](../includes/azure-appinsights-name.md)] resource. This telemetry data let's you identify and analyze where and why the error occurs. You can also set up alerts in [!INCLUDE[appInsights](../includes/azure-appinsights-name.md)] to get notified if many users experience errors.

There are three types of telemetry data emitted about errors

- Error message quality
- Error dialogs shown to users
- Permission errors 


| If you want to...| Then look at this telemetry |
|------------------|---------------------------- |
| Understand if users understand the error messages they see. | [Error message quality telemetry](../administration/telemetry-error-message-voting-trace.md) |
| Understand which error dialogs users see and where in the AL code the error is raised. | [Error method telemetry](../administration/telemetry-error-method-trace.md) |
| Understand when users get error dialogs about lack of permissions. | [Permission error telemetry](../administration/telemetry-permission-error-trace.md) |


## Error telemetry (emit your own)

You can emit your own telemetry about error situations by using the Telemetry AL module. Using this module, you can simplify the way you monitor the health of your app and also monitor the uptake and usage of application features. 

For more information, see [Telemetry.LogError](../administration/telemetry-feature-telemetry.md#LogError).


## See also

[Failure modeling and robust coding practices](devenv-robust-coding-practices.md)  
[Understanding the error dialog](devenv-error-dialog.md)   
[User experience guidelines for errors](devenv-error-handling-guidelines.md)  
[Actionable errors](devenv-actionable-errors.md)   
[Collecting errors](devenv-error-collection.md)   
[Handling errors using Try methods](devenv-handling-errors-using-try-methods.md)   
[Handling errors (in Page Background Tasks)](devenv-page-background-tasks.md#handling-errors)   
[Telemetry.LogError](../administration/telemetry-feature-telemetry.md#LogError)  
[Error message quality telemetry](../administration/telemetry-error-message-voting-trace.md)   
[Error method telemetry](../administration/telemetry-error-method-trace.md)  
[Permission error telemetry](../administration/telemetry-permission-error-trace.md)   
[AL control statements](devenv-al-control-statements.md)   
[AL development environment](devenv-reference-overview.md)   
