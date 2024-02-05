---
title: "OnPreReport (Report) Trigger"
description: "Runs before a report is run."
ms.author: solsen
ms.custom: na
ms.date: 06/23/2021
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)

# OnPreReport (Report) Trigger
> **Version**: _Available or changed with runtime version 1.0._

Runs before a report is run.


## Syntax
```AL
trigger OnPreReport()
begin
    ...
end;
```



[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  

This trigger runs after the request page is run. The table views and filters for the report data items are set while this trigger is run. As this trigger is run after the request page is processed, you have access to any filters the user has set. If you want to print the settings of these filters in the report, you can retrieve them using the following text string.  
  
```AL
ReportFilter := SomeRecord.GetFilters;  
```  
  
Use the ReportFilter text string as the source expression for a control in a section of the report.  

## See Also

[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  
[OnPreReport (Report Extension) Trigger](../reportextension/devenv-onprereport-reportextension-trigger.md)  
[Report Triggers and Runtime Operations](../../devenv-report-triggers.md)
