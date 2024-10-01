---
title: "OnNextRecord Trigger"
description: "OnNextRecord trigger in AL for Business Central."
ms.date: 04/01/2021
ms.topic: reference
author: SusanneWindfeldPedersen
---

# OnNextRecord Trigger

Determines the next record to be displayed.  

## Syntax  

```AL
trigger OnNextRecord(Steps): ActualSteps  
begin
    ...
end;
``` 

#### Parameters  
 *Steps*  

 \(Integer\) The number of records stepped through before displaying another record. A negative value indicates steps backwards.  

## Return Value  
 *ActualSteps*  

 \(Integer\) This return value contains the actual number of steps or records cycled through. The default value is zero \(0\).  

## Applies to  

- Pages  

## Remarks

This trigger is executed in place of the default next record behavior.  

If an error occurs in the trigger code, the page is closed.  

## See Also  

[Triggers](devenv-triggers.md)  
[Page and Action Triggers](devenv-page-and-action-triggers.md)  
[Page Properties](../properties/devenv-properties.md)