---
title: "TaskScheduler Data Type"
description: "Is a complex data type for creating and managing tasks in the task scheduler, which runs codeunits at scheduled times."
ms.author: solsen
ms.custom: na
ms.date: 12/15/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# TaskScheduler Data Type
> **Version**: _Available or changed with runtime version 1.0._

Is a complex data type for creating and managing tasks in the task scheduler, which runs codeunits at scheduled times.


## Static methods
The following methods are available on the TaskScheduler data type.


|Method name|Description|
|-----------|-----------|
|[CancelTask(Guid)](taskscheduler-canceltask-method.md)|Cancels and deletes a scheduled task that runs a specific codeunit.|
|[CanCreateTask()](taskscheduler-cancreatetask-method.md)|Checks whether it is possible to schedule tasks in this session.|
|[CreateTask(Integer, Integer [, Boolean] [, Text] [, DateTime] [, RecordId])](taskscheduler-createtask-integer-integer-boolean-string-datetime-recordid-method.md)|Adds a task to ensure that a codeunit is not run before the specified time.|
|[CreateTask(Integer, Integer, Boolean, Text, DateTime, RecordId, Duration)](taskscheduler-createtask-integer-integer-boolean-string-datetime-recordid-duration-method.md)|Adds a task to ensure that a codeunit is not run before the specified time.|
|[SetTaskReady(Guid [, DateTime])](taskscheduler-settaskready-method.md)|Sets a task that runs a codeunit to the ready state. The task will not run unless it is in the ready state.|
|[TaskExists(Guid)](taskscheduler-taskexists-method.md)|Checks whether a specific task exists.|


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## See also

[Task Scheduler Overview](../../devenv-task-scheduler.md)   
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  