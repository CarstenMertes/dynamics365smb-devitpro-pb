---
title: "OnInsertRecord Trigger"
description: "OnInsertRecord trigger in AL for Business Central."
ms.date: 04/01/2021
ms.topic: reference
author: SusanneWindfeldPedersen
---

# OnInsertRecord Trigger

Runs before a new record is inserted into the table.  

## Syntax  

```AL
trigger OnInsertRecord(BelowxRec): Ok
begin
    ...
end;
```  

#### Parameters

 *BelowxRec*  
 \(Boolean\) This return value indicates whether the new record is to be inserted after the last record in the table \(xRec\) or not. If **false**, the record is to be inserted between an existing record and the last record. If **true**, the record is to be inserted below the last record in the table \(xRec\).  

## Return Value

 *Ok*  
 \(Boolean\) Determines whether to insert a new record. The return value is checked after each call. If **true**, the record is inserted. If **false**, the record is not inserted.  
  
## Applies to  
  
- Pages  
  
## Remarks

If an error occurs in the trigger code, the action is canceled, but the page is not closed. The user cannot enter any new data and an error is shown in the message bar.  
  
## See Also  

[Triggers](devenv-triggers.md)  
[Page and Action Triggers](devenv-page-and-action-triggers.md)  
[Page Properties](../properties/devenv-properties.md)