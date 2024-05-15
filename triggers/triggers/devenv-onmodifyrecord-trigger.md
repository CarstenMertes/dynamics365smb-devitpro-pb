---
title: "OnModifyRecord Trigger"
description: "OnModifyRecord trigger in AL for Business Central."
ms.date: 04/01/2021
ms.topic: reference
author: SusanneWindfeldPedersen
---

# OnModifyRecord Trigger

Runs before a record is modified in the table.  

## Syntax  

```AL
trigger OnModifyRecord(): Ok
begin
    ...
end;
```   

## Return Value

 *Ok*  
  
 (Boolean) Indicates whether a record should be modified. The return value is checked after each  call. If **true**, the record is modified (default). If **false**, the record is not modified.  
  
## Applies to  
  
- Pages  
  
## Remarks  

If an error occurs in the trigger code, the action is canceled, but the page is not closed.  
  
You can write to the database using this trigger.  
  
## See Also  

[Triggers](devenv-triggers.md)  
[Page and Action Trigger](devenv-page-and-action-triggers.md)  
[Page Properties](../properties/devenv-properties.md)