---
title: Reports overview
description: Use reports to display information from database to structure and summarize information and print documents, such as invoices. 
ms.custom: na
ms.date: 12/05/2023
ms.reviewer: na
ms.topic: overview
author: SusanneWindfeldPedersen
ms.collection: get-started
---

# Reports overview

You can use reports to print or display information from a [!INCLUDE[prod_short](../includes/prod_short.md)] database. Use reports to structure and summarize information to print documents, such as invoices. For example, create a report that lists all customers and orders that are added by each customer. Also, create a report that's automatically filled with the relevant information for an invoice.  

Reports can also be used to process data without printing or displaying content. For example, use a report to automate updating all prices in an item list. It can be easier to create a report to process data instead of a codeunit to do the same processing because you can use:  

- Request page functionality to select options and filters for data items, which are available in a report but are difficult to add to a codeunit. For more information, see [Using request pages with reports](devenv-request-pages-for-reports.md). 

- Report data items instead of writing code to open tables and retrieve records.  

- Data modeling, which is available when you design reports. 

## Creating reports

Creating a report involves three tasks: 
1. design the dataset,
2. design the visual layout(s),
3. ensure users can discover and understand how to use the report.

First, you create a report object and design the dataset. The dataset determines the data that is extracted or calculated from the [!INCLUDE[prod_short](../includes/prod_short.md)] database tables that can be used in the report. 


When the dataset is created, you then design the visual layout of the report. There are three types of report layouts that you can create: layouts using report definition language (RDL), Word report layouts, and Excel report layouts. Each type of layout caters for different user needs - Excel is used for analytical reports, Word layouts are for document reports, and RDL is for advanced scenarios (both for document and analytical reports).

After you develop a report and before you make it available for users, you need to consider *discoverability* for the report, meaning:

- How users can discover that the report exists?
- Ensure that users can find it.
- Ensure that users know how to use it.

Another option is to extend the functionality of an existing report with a [Report Extension Object](devenv-report-ext-object.md) by adding columns to the existing report dataset, adding new data items, adding to the request page, or adding a new layout.

## Getting started

The following table includes links to help you get started with designing the reports.

|To      |See      | 
|--------|---------| 
|Learn the overview of the report design process|[Report Design Overview](devenv-report-design-overview.md)| 
|Understand the report structure and designing the layout for a report.|[Report Object](devenv-report-object.md)|
|Understand how to extend an existing report.|[Report Extension Object](devenv-report-ext-object.md)|
|Understanding the data model and dataset of a report|[Defining a Report Dataset](devenv-report-dataset.md)|  
|Learn how to create a report using a Word layout|[Creating a Word Layout Report](devenv-howto-report-layout.md)| 
|Learn how to create a report using an RDL layout report.|[Creating an RDL Layout Report](devenv-howto-rdl-report-layout.md)|
|Learn about creating a report based on an Excel layout.|[Creating an Excel Layout Report](devenv-howto-excel-report-layout.md)|
|Learn how to define multiple report layouts for one report.|[Defining Multiple Report Layouts](devenv-multiple-report-layouts.md)|
|Learn how to use request pages with reports.| [Using request pages with reports](devenv-request-pages-for-reports.md) |
|Learn how to help users discover the report.|[Report discoverability overview](devenv-reports-discoverability.md) |



## See also

[Report object](devenv-report-object.md)  
[Report extension object](devenv-report-ext-object.md)  
[Creating a report](devenv-howto-report-layout.md)  
[Using request pages with reports](devenv-request-pages-for-reports.md)   
[Creating an Excel layout report](devenv-howto-excel-report-layout.md)  
[Creating an RDL layout report](devenv-howto-rdl-report-layout.md)  
[Creating a Word layout report](devenv-howto-report-layout.md)  
[Defining multiple report layouts](devenv-multiple-report-layouts.md)  
[Utilizing Read Scale-Out for better performance](../administration/database-read-scale-out-overview.md)  