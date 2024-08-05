---
title: "OnPostDataItem Trigger"
description: "OnPostDataItem trigger in AL for Business Central."
ms.date: 04/01/2021
ms.topic: reference
author: SusanneWindfeldPedersen
---

# OnPostDataItem Trigger

Runs after a data item is processed.  

## Syntax

```AL
trigger OnPostDataItem() 
begin
    ...
end;
```  

## Applies to  

- Data items  
  
## Remarks

This trigger runs after the last record in the data item is processed but before the [OnPostReport Trigger](devenv-onpostreport-trigger.md) or the [OnPostXMLport Trigger](devenv-onpostxmlport-trigger.md) is executed, if it is the last data item of the report or XMLport.  
  
Use this trigger to perform any cleanup or post processing needed after a data item is processed. For example, if you create a non-printing report where records are updated, you can update all the records with the modification date like shown in the example below.  
  
```AL
ModifyAll("Modification Date",TODAY);   
```  
  
## See Also

[Triggers](devenv-triggers.md)  
[OnPostReport Trigger](devenv-onpostreport-trigger.md)  
[Report and Data Item Triggers](devenv-report-and-data-item-triggers.md)  