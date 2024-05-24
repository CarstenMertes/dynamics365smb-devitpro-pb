---
title: "OnAfterInsertRecord Trigger"
description: "OnAfterInsertRecord trigger in AL for Business Central."
ms.date: 04/01/2021
ms.topic: reference
author: SusanneWindfeldPedersen
---

# OnAfterInsertRecord Trigger

Runs after a record has been inserted into a database table.  
  
## Applies to  
- XMLports  
  
## Remarks  
 This trigger is only used to import data and can be used to move data from temporary tables to real tables.  
  
 If the [AutoSave Property](../properties/devenv-autosave-property.md) is **false**, then although the record is not inserted automatically, the OnAfterInsertRecord trigger is still called after the insertion would have occurred.  
  
## See Also  
 [Triggers](devenv-triggers.md)  
 [AutoSave Property](../properties/devenv-autosave-property.md)  
 [XMLport Triggers](devenv-xmlport-triggers.md)  
 [OnBeforeInsertRecord Trigger](devenv-onbeforeinsertrecord-trigger.md)  