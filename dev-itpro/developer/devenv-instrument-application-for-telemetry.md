---
title: Developing telemetry into your Business Central application
description: This article describes how to add code to application objects that enables you to gather telemetry.
ms.custom: na
ms.date: 05/24/2022
ms.reviewer: na
ms.topic: conceptual
author: jswymer
---
# Instrumenting an application for telemetry

This article describes how you can implement custom telemetry signals in your application for emitting telemetry data. This data can then be collected and visualized for analyzing the application against the desired business goals, troubleshooting, and more.

## Telemetry overview

One aspect of event logging is the data collection about the working and deployment infrastructure of an application to diagnose conditions and troubleshoot problems that affect its operation and performance. For example, this type of event logging includes [!INCLUDE[server](includes/server.md)] events and trace events like SQL and AL method (function) traces.

Another aspect of logging is *telemetry*, which is the collection of data about how your application works in production. Telemetry can tell you about specific activities that users perform within the application in the production environment. Telemetry also helps troubleshooting in those instances where you aren't able to reproduce the conditions experienced by the user or have no access to the user's environment. Telemetry can be divided into different categories, like: telemetry for engineering, telemetry about the business, telemetry for customers.

## Creating custom telemetry signal

There are two different resources where telemetry trace signals can be sent for monitoring and analyzing: Event Log and Microsoft Azure Application Insights. By default, the [!INCLUDE[prod_short](includes/prod_short.md)] application is instrumented to emit several system telemetry trace signals to these destinations. Custom telemetry trace signals enable you to send telemetry data from anywhere in the application code to either of these destinations.

The procedure for creating custom telemetry signals is different for each resource. Your choice might also depend on whether you're developing for [!INCLUDE[prod_short](../developer/includes/prod_short.md)] online or on-premises.

|Resource|Description|Online|On-premises|More information|
|-----------|-----------|------|-----------|----------------|
|Application Insights|Create custom telemetry signals that are sent to an Application Insights resource in Azure. [Application Insights](/azure/azure-monitor/app/app-insights-overview) is a service hosted within Azure that gathers telemetry data for analysis and presentation. <br /><br />Extension developers can specify whether the signal is only sent to the extension publisher or also to the VAR partner telemetry resource.<br /><br />You create these custom trace signals by using the LOGMESSAGE method in the code.|![check mark for feature.](media/check.png)|![check mark for feature](media/check.png)|[See...](devenv-instrument-application-for-telemetry-app-insights.md)|
|Event Log| Create custom telemetry trace signals that are sent to the Event Log of the [!INCLUDE[server](includes/server.md)] machine. You create these custom trace signals by using the [SENDTRACETAG method](methods-auto/session/session-sendtracetag-method.md) in the code.||![check mark for feature.](media/check.png)|[See...](devenv-instrument-application-for-telemetry-event-log.md)|

> [!NOTE]
> Using Application Insights is recommended. 

## See Also

[Monitoring and Analyzing Telemetry](../administration/telemetry-overview.md)  
[Monitoring Business Central Server Events](../administration/monitor-server-events.md)  
