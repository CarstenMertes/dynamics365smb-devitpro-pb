---
title: "OnAfterGetRecord Trigger"
description: "OnAfterGetRecord trigger in AL for Business Central."
ms.date: 04/01/2021
ms.topic: reference
author: SusanneWindfeldPedersen
---

# OnAfterGetRecord Trigger

Runs after a record is retrieved from a table, but before it is displayed to the user.  

## Applies to

- Pages  

## Syntax  

```AL
trigger OnAfterGetRecord()
begin
    ...
end;
``` 
  
## Remarks  

Use this trigger to calculate variables that depend on the current record. 

This trigger is independent of the currently selected record in the UI. When it gets raised depends on when the UI needs to load more data and the block size of the data read. So, for example, in a list page, where rows are read in larger blocks, then the `OnAfterGetRecord` trigger will be raised for each of the records read before the page is shown.

Within the trigger, the `Rec` variable will refer to the record just read.
  
If there is an error in the trigger code, then the page is closed.
  
## See Also  

[Triggers](devenv-triggers.md)  
[Page and Action Triggers](devenv-page-and-action-triggers.md)  
