---
title: "Disable Logging Events to the Windows Application Log"
description: For Business Central on-premises, you can configure the event logs. 
ms.custom: bap-template
ms.date: 04/01/2021
ms.reviewer: jswymer
ms.topic: conceptual
author: SusanneWindfeldPedersen
ms.service: dynamics-365-op
---

# Disable Logging Events to the Windows Application Log

Because the [!INCLUDE[server](../developer/includes/server.md)] events are always logged to the Application and Services Logs, you can disable logging [!INCLUDE[s[!INCLUDE[server](../developer/includes/server.md)]e Windows Application log and not lose any data. The Windows Application log contains events from several applications and components. Disabling logging to the Windows Application log enables you to limit the amount of data that is stored.  
  
> [!IMPORTANT]  
> If you are using System Center Operations Manager to monitor [!INCLUDE[server](../developer/includes/server.md)] do not disable logging to the Windows Application log. If you do, monitoring will not work.  
  
To disable logging to the Windows Applications Log, you can use the [!INCLUDE[admintool](../developer/includes/admintool.md)] or modify the [!INCLUDE[server](../developer/includes/server.md)] configuration file \(CustomSettings.config\).  
  
## To configure custom telemetry logging to the Windows Application log by using the [!INCLUDE[admintool](../developer/includes/admintool.md)]  
  
1. To start the [!INCLUDE[admintool](../developer/includes/admintool.md)], choose **Start**, and in the **Search programs and files** box, type **[!INCLUDE[prod_short](../developer/includes/prod_short.md)] Administration**, and then choose the related link.  
  
2. In the left pane, under **Console root**, select the [!INCLUDE[server](../developer/includes/server.md)] 
  
3. In the center pane, choose the **Edit** button.  
  
4. Under **General**, clear the **Enable Event Logging to Windows Application Log** check box.  
  
5. Choose the **Save** button, and then choose the **OK** button.  
  
   You must restart the [!INCLUDE[server](../developer/includes/server.md)]or the changes to take effect.  
  
6. To restart, the [!INCLUDE[server](../developer/includes/server.md)]in the left pane, select the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] computer.  
  
   Unless you are administering a remote computer, this is [!INCLUDE[prod_short](../developer/includes/prod_short.md)] \(local\).  
  
7. In the center pane, right-click an instance, and then choose **Restart**.  
  
## To disable logging to the Windows Application log by modifying the CustomSettings.config file  
  
1. Open the CustomSettings.config file for the [!INCLUDE[server](../developer/includes/server.md)]n a text editor, such as Notepad.  
  
     By default, the file is located in the [!INCLUDE[prodinstallpath](../developer/includes/prodinstallpath.md)]\\Service folder or [!INCLUDE[prodinstallpath](../developer/includes/prodinstallpath.md)]\\Service\\Instances\\\<instancename> folder \(for multitenant installations\).  
  
2. Set the **EnableApplicationChannelLog** setting to **false**.  
  
3. Save the file, and then restart the [!INCLUDE[server](../developer/includes/server.md)] 
  
## See Also

[Monitoring Business Central Server Events Using Event Viewer](monitor-server-events-windows-event-log.md)  
[Monitoring Business Central Server Events](monitor-server-events.md) 