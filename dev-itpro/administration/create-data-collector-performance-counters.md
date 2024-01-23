---
title: Create Data Collector for Performance Counters
description: This topic describes how to create a Data Collector Set in Performance Monitor that contains Microsoft Dynamics365 Business Central performance counters.
ms.custom: bap-template
ms.date: 04/01/2021
ms.reviewer: jswymer
ms.service: dynamics-365-op
ms.topic: conceptual
ms.assetid: 2b2c8383-8e5a-47ea-bfd0-8621021a697a
caps.latest.revision: 9
---
# Creating a Data Collector for Business Central Performance Counters
This topic describes how to create a Data Collector Set in Performance Monitor that contains [!INCLUDE[prod_short](../developer/includes/prod_short.md)] performance counters.  
  
### To create a Data Collector Set for [!INCLUDE[prod_short](../developer/includes/prod_short.md)] performance counters  
  
1.  On the computer that is running [!INCLUDE[server](../developer/includes/server.md)], start Performance Monitor.  
  
    -   Choose **Start**, in the **Search** box, type **perfmon**, and then choose the related link.  
  
2.  In the navigation pane, expand **Data Collector Sets**, right-click **User-defined**, choose **New**, and then choose **Data Collector Set**.  
  
3.  On the **Create new Data Collector Set Wizard** page, enter a name for the new data collector set. Select **Create manually \(Advanced\)**, and then choose the **Next** button.  
  
4.  On the **What type of data do you want to include** page, select the **Performance counter** check box, and then choose the **Next** button.  
  
5.  In the **Add Counters** window, in the **Select counters from computer:** drop-down list, choose the computer that is running [!INCLUDE[server](../developer/includes/server.md)].  
  
6.  In the **Available counters** list, expand **[!INCLUDE[prod_short](../developer/includes/prod_short.md)]**, and select one or more counters.  
  
7.  In the **Instances of selected object** list, select **\<All instances>** to collect data for all [!INCLUDE[server](../developer/includes/server.md)] instances on the computer or individually select one or more instances from the list.  
  
8.  Choose the **Add** button, and then choose the **OK** button  
  
9. Choose the **Next** button.  
  
10. On the **Where would you like the data to be saved page** page, set **Root directory** to the location to store the log file that will contain data that is collected by the Data Collector Set.  
  
11. Choose the **Finish** button to save the Data Collector Set and exit.  
  
     To see the new Data Collector Set, in the navigation pane, expand **Data Collector Sets**, and then expand **User Defined**. You can start to collect data.  
  
##  <a name="StartDataCollectorSet"></a> To start and stop a Data Collector Set  
  
-   To start to collect data immediately, under **Data Collector Sets**, expand **User Defined**, right-click the Data Collector Set, and then choose **Start**.  
  
-   To stop collecting data, right-click the Data Collector Set, and then choose **Stop**.  
  
 For information about how to schedule a time to start and stop collecting data, see [Schedule Data Collection in Windows Performance Monitor](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc722312(v=ws.11)).  
  
 For information about how to view the data that is collected by the Data Collector Set, see [View Performance Counter Data for a Data Collector Set](monitor-view-performance-counter-data-for-data-collector-set.md).  
  
## See Also  
 [Working with Data Collector Sets](monitor-work-with-data-collector-sets.md)   
 [Create a Data Collector Set From Template](monitor-create-data-collector-set-from-template.md)   
 [Business Central Performance Counters](performance-counters.md)