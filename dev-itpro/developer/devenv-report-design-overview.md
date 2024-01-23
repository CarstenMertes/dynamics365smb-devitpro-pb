---
title: Report Design Overview
description: Design a report by defining the dataset and designing the layout. Report object is composed of dataset, layout, request page, properties, triggers and code.
author: SusanneWindfeldPedersen
ms.custom: bap-template
ms.date: 12/08/2023
ms.reviewer: jswymer

ms.topic: overview
ms.author: solsen
---

# Report Design Overview

A report in [!INCLUDE[prod_long](includes/prod_long.md)] is composed of the following items:  

- A report object
- A report dataset
- A report layout
- A request page
- Properties, triggers, and code 

You design a report by first defining the dataset, then designing the visual layout, and finally a request page.

## Report object  

You create a report object in the [!INCLUDE[d365_dev_long_md](includes/d365_dev_long_md.md)] to define the data model, or dataset of a report. You can structure and summarize information in a report and print documents, such as sales quotes and invoices. For more information, see [Report Object](devenv-report-object.md).  

## Report dataset

In order to define the underlying data model, you use the report dataset. A report dataset determines the data that is extracted or calculated from the [!INCLUDE[prod_short](includes/prod_short.md)] database tables that can be used in a report. You build the report dataset by adding data items and columns. For more information, see [Report Dataset](devenv-report-dataset.md). You can also extend a dataset from an existing report, to add more columns for example. For more information, see [Report Extension Object](devenv-report-ext-object.md).

[!INCLUDE[intelli_shortcut](includes/query_as_a_report_datasource.md)]

## Report layouts  

The visual layout determines the content and format of a report when it is viewed and printed. You build the layout of a report by arranging data items and columns and specifying the general format, such as text font and size. A report that is viewed, printed, or saved from a [!INCLUDE[prod_short](includes/prod_short.md)] client must have a report layout. 

There are three types of report layouts: Excel report layouts, Word report layouts, and layouts using report definition language (RDL). You can also extend an existing report, for example, to add a new layout. For more information, see [Report Extension Object](devenv-report-ext-object.md).

> [!NOTE]  
> The layout in a *report extension* will not automatically be used when the report extension is deployed. To use the report extension layout, in [!INCLUDE [prod_short](includes/prod_short.md)], go to the **Report Layout Selection** page to choose to use the new layout for the report in question by choosing it from the **Custom Layout Description** drop-down box.

### Excel report layout

You create and edit Excel layouts by using Microsoft Excel. An Excel report layout is based on an Excel (.xlsx) document and provides end users to take advantage of the capabilities in Excel such as sliders, diagrams, charts, pivot tables, and PowerQuery to design the report. For more information, see [Creating an Excel Layout Report](devenv-howto-excel-report-layout.md).

### Word report layout

You create and edit Word layouts by using Microsoft Word. A Word layout is based on a Word document that includes a custom XML parts that represents the report dataset. For more information, see [Creating a Word Layout Report](devenv-howto-report-layout.md).  

### RDL layout 

To create an RDL layout report, you use Visual Studio Report Designer or Microsoft SQL Server Reporting Services Report Builder. For more information, see [Creating an RDL Layout Report](devenv-howto-rdl-report-layout.md).

[!INCLUDE[RDL_layout_performance](includes/include-rdl-performance.md)]

## Report request page
A request page is a page that is run before the report starts to execute. Request pages enable end users to specify options and filters for the report. For more information, see [Using request pages with reports](devenv-request-pages-for-reports.md).

## Report properties, triggers, and code 
You can control the way the AL runtime and client work on the report by setting properties on the report object. For a list of all properties that you can set on the report object, see the AL language reference article [Report, Report Fields, and Report Extension Properties](properties/devenv-report-property-overview.md).

With report triggers, you can control how the reporting feature works in [!INCLUDE[prod_short](includes/prod_short.md)], for example to control post-processing or printing of report documents. For more information, see [Report Triggers and Runtime Operations](devenv-report-triggers.md).


## See Also  

[Reports](devenv-reports.md)  
[Report object](devenv-report-object.md)  
[Report extension object](devenv-report-ext-object.md)  
[Report dataset](devenv-report-dataset.md)   
[Using request pages with reports](devenv-request-pages-for-reports.md)  
[Creating an Excel layout report](devenv-howto-excel-report-layout.md)   
[Creating an RDL layout report](devenv-howto-rdl-report-layout.md)  
[Creating a Word layout report](devenv-howto-report-layout.md)   
[Report, report fields, and report extension properties](properties/devenv-report-property-overview.md)   
[Report triggers and runtime operations](devenv-report-triggers.md)  
