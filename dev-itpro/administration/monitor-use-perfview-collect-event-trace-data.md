---
title: Use PerfView to Collect Event Trace Data
description: Get tips for how to use PerView on telemetry traces.
ms.custom:
  - bap-template
  - evergreen
ms.date: 10/26/2024
ms.update-cycle: 1095-days
ms.reviewer: jswymer
ms.service: dynamics-365-op
ms.topic: how-to
author: SusanneWindfeldPedersen
---
# Use PerfView to Collect Event Trace Data

[!INCLUDE[on_prem_only_v2](../developer/includes/on_prem_only_v2.md)]

This topic describes how to use PerfView to collect event trace data for [!INCLUDE[server](../developer/includes/server.md)]. When you collect event trace data, the data is stored in an event trace log \(.etl\) file in a location that you select.  
  
## To install PerfView 
  
-  Go to [https://go.microsoft.com/fwlink/?LinkID=313428](https://go.microsoft.com/fwlink/?LinkID=313428), and then follow the instructions to download and install PerfView.  
  
### To collect event trace data  
  
1. Open PerfView.exe.  
  
2. On the **Collect** menu, select **Collect**.  
  
   The **Collecting data over a user specified interval** dialog box appears.  
  
3. Set the **Data file** field to the path and name of the log file in which to store the trace event data. The file name must have the .etl file name extension.  
  
4. Select **Advanced options**.  
  
   The upper part of the **Advanced options**area includes check boxes and fields that specify the providers from which to collect event trace data.  
  
5. In the **Additional providers** field, type **Microsoft-DynamicsNAV-Server**.  
  
    - If you want to filter on a specific trace event, include a colon after **Microsoft-DynamicsNAV-Server**, followed by the hexadecimal keyword value for the trace event. For example, to collect trace events data on service call trace events only, then type  **Microsoft-DynamicsNAV-Server:0x4**.  
  
    - If you want to collect data on more than one trace event, add the keyword values for each trace event and then use the sum in the field. For example, if you want to collect data on service calls \(keyword value = 0x4\) and AL function traces \(keyword value = 0x8\), then type **Microsoft-DynamicsNAV-Server:0xC** in the field. In hexadecimal, the sum of 0x4 and 0x8 is 0xC.  
  
6. Clear the check boxes above the **Additional providers** field for any providers that you do not want to collect data for.  
  
7. To start recording data, select the **Start Collection** button.  
  
8. To stop recording data, select the **Stop Collection** button.  
  
The collected event trace data is stored in an event trace log \(.etl\) file in the location that you specified. You can view the data in the log file by using various industry-standard tools, such as PerfView. For information about how to use PerfView to view the event trace data, see [Use PerfView to View Event Trace Data](monitor-use-perfview-view-event-trace-data.md).  
  
##  <a name="ViewDataPerfView"></a> To view event trace data from an event trace log file  
  
1. Open PerfView.exe.  
  
2. In PerfView, use the left pane to locate the .etl file that you want to view.  
  
   The left pane displays the current directory and the files that PerfView is set up to browse. To change a directory, select a subdirectory from the list or type the directory \(for example, c:\\PerfLogs\) in the text box at the top of the pane.  
  
3. Double-click the .etl file that you want to view.  
  
   Several items appear in the left pane under the .etl file that you selected.  
  
4. To view the event traces, double-click **Events**.  
  
     The **Events** window opens to display the contents of the .etl file. Trace events are listed in the left pane.  
  
5. To view details about a trace event, double-click the trace event.  
  
## Related information

[Monitoring Business Central Server Events](monitor-server-events.md)  
[Business Central Server Trace Events](server-trace-events.md)  
[Instrumenting an Application for Telemetry](../developer/devenv-instrument-application-for-telemetry.md)  
