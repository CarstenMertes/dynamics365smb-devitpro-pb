---
title: Use Performance Monitor to Collect Event Trace Data
description: Get tips for how to use Performance Monitor on telemetry traces.
ms.custom:
  - bap-template
  - evergreen
ms.date: 10/26/2024
ms.update-cycle: 1095-days
ms.reviewer: jswymer
ms.service: dynamics-365-op
ms.topic: how-to
author: jswymer
---
# Use Performance Monitor to collect event trace data

[!INCLUDE[on_prem_only_v2](../developer/includes/on_prem_only_v2.md)]

This topic describes how to use Windows Performance Monitor to collect event trace data for [!INCLUDE[server](../developer/includes/server.md)]. To collect trace event data, you create a Data Collector Set, and then start the Data Collector Set.  
  
## Create a data collector set for collecting [!INCLUDE[prod_short](../developer/includes/prod_short.md)] trace event data  
  
1. Start Windows Performance Monitor.  
  
    - Select **Start**, in the **Search** box, type **perfmon**, and then select the related link.  
  
2. In the navigation tree, expand **Data Collector Sets**, right-click **User-defined**, select **New**, and then select **Data Collector Set**.  
  
3. On the **Create new Data Collector Set Wizard** page, enter a name for the new data collector set, select **Create manually \(Advanced\)**, and then select the **Next** button.  
  
4. On the **What type of data do you want to include** page, select the **Event trace data** check box, and then select the **Next** button.  
  
5. On the **Which event trace providers would you like to enable** page, select the **Add** button to add a provider.  
  
6. In the **Event Trace Providers** list, select **Microsoft-DynamicsNAV-Server**, and then select the **OK** button.  
  
7. If you want to collect data for all trace events, select the **Next** button. If you want to collect data on specific trace events, do the following:  
  
    1. In the **Properties** list, select **Keywords \(Any\)**, and then select the **Edit** button.  
  
    2. On the **Property** page, in the **Manual** box, type the keyword decimal value for the trace event. For a list of keyword values for trace events, see [Business Central Server Trace Events](server-trace-events.md).  
  
        For example, if you want to collect data on service call trace events, then type **4**. If you want to collect data on more than one trace event, add the keyword values for each trace event and then use the sum in the **Manual** box. For example, if you want to collect data on service calls \(keyword decimal value = 4\) and AL functions \(keyword decimal value = 8\), then use the value **12**.  
  
        > [!NOTE]  
        > Performance Monitor will automatically convert the value to hexadecimal, such as 0x4 or 0xC. You can also enter the keyword hexadecimal values directly.  
  
    3. Select the **OK** button, and then **Next** button.  
  
8. On the **Where would you like the data to be stored** page, set the **Root directory** box to the folder where you want to save the event trace log file that is generated when you run the Data Collector Set.  
  
9. Select the **Finish** button to complete the wizard  
  
     The new Data Collector Set appears under **User Defined** in the navigation pane.  
  
 Complete the next procedure to increase trace buffer settings to make sure that events are not dropped when collecting trace event data.  
  
## Change the data collector set trace buffers  
  
1. In the navigation pane, select the new Data Collector Set.  
  
2. In the main pane, right-click the **DataCollector01** item, and then select **Properties**.  
  
3. In the **Properties** dialog box, select the **Trace Buffers** tab.  
  
4. Set the following properties.  
  
    |Property|Recommended minimum values|  
    |--------------|--------------------------------|  
    |Buffer size|128|  
    |Minimum buffers|50|  
    |Maximum buffers|50|  
  
     You might have to adjust these properties based on the monitoring sessions and expected number of events that will be collected. If a large number of events are collected, then the trace buffer size and count might have to be increased.  
  
5. Select the **OK** button to save and close the **Properties** dialog box.  
  
##  <a name="StartDataCollectorSet"></a> To start and stop a Data Collector Set  
  
-  To start to collect data, right-click the Data Collector Set, and then select **Start**.  
  
-  To stop collecting data, right-click the Data Collector Set, and then select **Stop**.  
  
For information about how to schedule a time to start and stop collecting data, see [Schedule Data Collection in Windows Performance Monitor](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc722312(v=ws.11)).  
  
The collected event trace data is stored in an event trace log \(.etl\) file in the location that you specified. You can view the data in the log file by using various industry-standard tools, such as PerfView. Learn more about how to use PerfView to view the event trace data in [Use PerfView to View Event Trace Data](monitor-use-perfview-view-event-trace-data.md).  
  
## Related information

[Monitoring Business Central Server events](monitor-server-events.md)  
[Use PerfView to view event trace data](monitor-use-perfview-view-event-trace-data.md)  
[Instrumenting an application for telemetry](../developer/devenv-instrument-application-for-telemetry.md)  
