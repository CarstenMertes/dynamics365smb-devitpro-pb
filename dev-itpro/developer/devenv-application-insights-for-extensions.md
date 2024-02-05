---
title: Sending Extension Telemetry to Azure Application Insights 
description: Describes how to configure an extension to send telemetry data to Azure Application Insights. 
ms.custom: na
ms.date: 04/01/2021
ms.reviewer: na
ms.topic: conceptual
author: jswymer
---

# Sending App/Extension Telemetry to Azure Application Insights

[!INCLUDE[2020_releasewave2.md](../includes/2020_releasewave2.md)]

This article describes how to set up an extension to send telemetry data to [!INCLUDE[appinsights](../includes/azure-appinsights-name.md)] for monitoring and analyzing. [!INCLUDE[prod_short](includes/prod_short.md)] emits telemetry data for several operations that occur when extension code is run. For an overview about the telemetry with [!INCLUDE[appinsights](../includes/azure-appinsights-name.md)], see [Monitoring and Analyzing Telemetry](../administration/telemetry-overview.md).

This feature targets publishers of per-tenant or appsource extensions to give them insight into issues in their extensions before partners and customers report them. Note that you get data for all customers across the install base of the app/extension.

## Get an Application Insights resource in Azure

The first thing to do is to create an Application Insights resource in Azure if you don't have one. For more information, see [Create an Application Insights resource](/azure/azure-monitor/app/create-new-resource).

The [!INCLUDE[appinsights](../includes/azure-appinsights-name.md)] resource is assigned a connection string, which you can see on the **Overview** page for the resource in Azure. Copy this connection string because you'll need it to enable telemetry in the app/extension.

## Add the Application Insights information to the app/extension

The next step is to add the `"applicationInsightsConnectionString"` setting the extension's app.json as shown:

```json
"applicationInsightsConnectionString": "<connection string>"
```

Replace `<connection string>` with the string that you copied in the [!INCLUDE[appinsights](../includes/azure-appinsights-name.md)] overview. For more information about the format of the [!INCLUDE[appinsights](../includes/azure-appinsights-name.md)] connection string, see [Connection Strings](/azure/azure-monitor/app/sdk-connection-string?tabs=net).

When done, build the extension package, then publish and install it as usual. When the extension is run from [!INCLUDE[prod_short](includes/prod_short.md)], [!INCLUDE[appinsights](../includes/azure-appinsights-name.md)] gathers the telemetry data for viewing and analyzing.

### Prior to runtime version 7.2

Up until runtime version 7.2 you cannot use the `"applicationInsightsConnectionString"` setting. Instead you have to use the `"applicationInsightsKey"` setting which is added using only the instrumentation key from the [!INCLUDE[appinsights](../includes/azure-appinsights-name.md)] connection string as shown:

```json
"applicationInsightsKey": "<instrumentation key>"
```

Where `<instrumentation key>` is replaced by the key denoted in the connection string as `InstrumentationKey=<instrumentation key>;<some other parameters>`.

> [!NOTE]
> Transition to using connection strings for data ingestion in [!INCLUDE[appinsights](../includes/azure-appinsights-name.md)] by **31 March 2025**. On 31 March 2025, technical support for instrumentation key–based global ingestion in the [!INCLUDE[appinsights](../includes/azure-appinsights-name.md)] feature of Azure Monitor will end. After that date, your [!INCLUDE[appinsights](../includes/azure-appinsights-name.md)] resources will continue to receive data, but Microsoft no longer provide updates or customer support for instrumentation key–based global ingestion. 

## Data in app/extension telemetry 
Currently, [!INCLUDE[prod_short](../developer/includes/prod_short.md)] offers telemetry on the following operations (the column _Extension support_ shows the types of events that are emitted to app/extension telemetry):  

[!INCLUDE[prod_short](../includes/include-telemetry-by-area.md)]


## See Also  
[Get Started with AL](devenv-get-started.md)  
[Publishing and Installing Extensions](devenv-how-publish-and-install-an-extension-v2.md)  
[JSON Files](devenv-json-files.md)
[Viewing telemetry data in Application Insights](../administration/telemetry-overview.md)  
[LogMessage Method](../developer/methods-auto/session/session-logmessage-string-string-verbosity-dataclassification-telemetryscope-string-string-string-string-method.md)  
