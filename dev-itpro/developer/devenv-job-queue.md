---
title: Job queue
description: Learn about how the job queue works
ms.custom: na
ms.date: 12/18/2023
ms.reviewer: na
ms.topic: conceptual
author: jswymer
---

# Job queue

This article describes how the job queue works in [!INCLUDE[prod_short](includes/prod_short.md)]. A job queue is basically an abstraction that uses the [task scheduler](devenv-task-scheduler.md) from the platform to enable end users to view, create, or modify jobs that are set to run in the background. These jobs can be set to run on a recurring schedule.

For information about how users work with the job queue in the client, see [Use job queues to schedule tasks](/dynamics365/business-central/admin-job-queues-schedule-tasks).

[!INCLUDE[async_note](includes/include-async-note.md)]

## Job queue flow

The following diagram illustrates the flow of the job queue:

[ ![Shows the job queue activity flow.](media/job-queue-activity-flow.png) ](media/job-queue-activity-flow.png)

<!--
## Create and manage job queue



.. Add some examples
-->
## How job queue works

This section describes the flow that a job queue goes through.

### General flow

A job is run when the task scheduler's task is run. For more information, see [Task scheduler - detailed flow](devenv-task-scheduler.md#detailed-flow).

Here's a general overview of the process:

1. When a job queue is created and set to ready state, a scheduled task is created to run, but not before the **Earliest Start Date/Time**.
2. When the scheduled task is picked up by the task scheduler to run, a new background session is started.
3. The background session is run by the **Job Queue Dispatcher** codeunit:
    1. It first checks whether the job should be run or rescheduled.

        If the job shouldn't run, it's deleted. Or, in the case of an already running "Category Code", it's rescheduled.
    2. The job queue entry is updated to the **In-Progress** state, and a job queue log entry is created.
    3. The specified **Object ID to Run** is then started.

       If an exception occurs, none of the subsequent steps in the Job Queue Dispatcher path will be run, but instead, the failure codeunit path will be run.
4. The failure codeunit path runs as follows:
    1. An exception is raised and surfaced.
    2. The **Job Queue Error Handler** codeunit is run in a new background session.
        1. The job queue entry is updated to the **Error** state.
        2. The errors are saved by using **Error Message Management**.
        3. The job queue entry and job queue log entry are updated with the error.
        4. The job queue then either stays in the **Error** state or is rescheduled:
            - It stays in **Error** state if the **Maximum No. of Attempts** value has been exceeded and it's not a recurring job.
            - It's rescheduled if the **Maximum No. of Attempts** value hasn't been exceeded and it's a recurring job.

## Running codeunits with the job queue

When running a codeunit with the job queue, you must declare the `OnRun()` trigger, as this defines the code, which the underlying task scheduler will run. The same applies for the failure codeunit.

```AL
codeunit 50142 MyCodeunitToBeRunFromTheJobQueue
{
    trigger OnRun()
    var
        // declare your variables
    begin
        // code to be run. Probably calling other methods
    end;
}
```

[!INCLUDE[gui_allowed](includes/include-gui-allowed.md)]

If you want to do multiple things with a single codeunit using the job queue, consider using a parameter. To achieve this, define the `TableNo` property and set it to "Job Queue Entry" on the codeunit, then you'll be able to access the parameter string defined on the job queue entry from the codeunit. 

```AL
codeunit 50143 MyCodeunitToBeRunFromTheJobQueueNowWithParameters
{
    TableNo = "Job Queue Entry";

    trigger OnRun()
    var
        // declare your variables
    begin
        if Rec."Parameter String" <> '' then
        begin
            // code to be run. Probably calling other methods
        end
    end;
}
```

### AL methods that throw nonretriable exceptions in job queue entries

When running codeunits in the job queue, you must make sure that the AL code doesn't assume the ability to interact with a user through the UI. You can use the [GuiAllowed Method](../developer/methods-auto/system/system-guiallowed-method.md) to suppress UI interactions. 

[!INCLUDE[callback_exception_no_ui_note](../includes/include-callback-exception-no-ui-note.md)]

[!INCLUDE[callback_exceptions_no_ui](../includes/include-callback-exceptions-no-ui.md)]

## About job queue sessions and permissions

The session runs using the same user/credentials that are used when calling AL code. The user that's used is the user that sets the job to ready state. The user must have appropriate permissions to run the job queue and any other objects that are associated with the operation of the specified object.

For more information about assigning permissions, see [Assign Permissions to Users and Groups](/dynamics365/business-central/ui-define-granular-permissions) in the business functionality help.

## Job queues and performance

[!INCLUDE[job_queue_performance](../includes/include-task-job-queue-performance.md)]

## Monitor and troubleshoot

[!INCLUDE[prod_short](includes/prod_short.md)] offers two ways to monitor the flow of job queues: Azure Application Insights and the Session Event table. These tools let you follow the execution of a job and investigate errors in failure codeunits.

### Job queue telemetry in Azure Application Insights

You can set up [!INCLUDE[prod_short](includes/prod_short.md)] to send telemetry traces to an [!INCLUDE[azure-appinsights-name](../includes/azure-appinsights-name.md)] resource in Azure. Once set up, telemetry data will be sent to the resource as job queue moves through the flow. For more information, see:

[Enable Sending Telemetry to Application Insights](../administration/telemetry-enable-application-insights.md) 

> [!NOTE]  
> Job queue telemetry in Azure Application Insights also works for [!INCLUDE[prod_short](includes/prod_short.md)] on-premises

#### Job queue telemetry

[!INCLUDE[job_queue_telemetry](../includes/include-telemetry-job-queue.md)]

[!INCLUDE[job_queue_telemetry_events](../includes/include-telemetry-job-queue-events.md)]

For more information about job queue telemetry, see [Analyzing Job Queue Telemetry](../administration/telemetry-job-queue-lifecycle-trace.md)

#### Task scheduler telemetry

[!INCLUDE[task_scheduler_telemetry](../includes/include-telemetry-task-scheduler.md)]

For more information about task scheduler telemetry, see [Analyzing Task Scheduler Telemetry](../administration/telemetry-task-scheduler-trace.md)

### Session Event Table

From the [!INCLUDE[prod_short](includes/prod_short.md)] web client, you can open the Session Events table by adding `table=2000000111` to the URL. For example: [https://businesscentral.dynamics.com/?table=2000000111](https://businesscentral.dynamics.com/?table=2000000111).

## Characteristics of job queues and scheduled tasks

[!INCLUDE[jobqueue-and-task-scheduler-characteristics](includes/include-jobqueue-and-task-scheduler-characteristics.md)]


## See also

[Use Job Queues to Schedule Tasks](/dynamics365/business-central/admin-job-queues-schedule-tasks)   
[Analyzing Job Queue Telemetry](../administration/telemetry-job-queue-lifecycle-trace.md)   
[Task Scheduler](devenv-task-scheduler.md)   
[Async processing overview](devenv-async-overview.md)   
[Performance Articles for Developers](../performance/performance-developer.md)   
[Developing Extensions](devenv-dev-overview.md)  
[Get Started with AL](devenv-get-started.md)  