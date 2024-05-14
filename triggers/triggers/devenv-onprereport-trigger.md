---
title: "OnPreReport Trigger"
description: "OnPreReport trigger in AL for Business Central."
ms.date: 04/01/2021
ms.topic: reference
author: SusanneWindfeldPedersen
---

# OnPreReport Trigger

Runs before a report is run.  

## Syntax

```AL
trigger OnPreReport() 
begin
    ...
end;
``` 
 
## Applies to

- Report objects
- Report extension objects
  
## Remarks  

This trigger runs after the request page is run. The table views and filters for the report data items are set while this trigger is run. As this trigger is run after the request page is processed, you have access to any filters the user has set. If you want to print the settings of these filters in the report, you can retrieve them using the following text string.  
  
```AL
ReportFilter := SomeRecord.GetFilters;  
```  
  
Use the ReportFilter text string as the source expression for a control in a section of the report.  
  
## See Also  

[Triggers](devenv-triggers.md)  
[GetFilters Method Record](../methods-auto/record/record-getfilters-method.md)  
[Report and Data Item Triggers](devenv-report-and-data-item-triggers.md)