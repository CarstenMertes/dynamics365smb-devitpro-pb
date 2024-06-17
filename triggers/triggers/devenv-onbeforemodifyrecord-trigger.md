---
title: "OnBeforeModifyRecord Trigger"
description: "OnBeforeModifyRecord trigger in AL for Business Central."
ms.date: 04/01/2021
ms.topic: reference
author: SusanneWindfeldPedersen
---

# OnBeforeModifyRecord Trigger
Runs after a record is read from the input stream and before the existing record in the database is modified.  
  
## Applies to  
- XMLports  
  
## Remarks  
 This trigger is used when you import data from an XMLport and then update an existing record in a table with the data from the XMLport.  
  
 If the [AutoSave Property](../properties/devenv-autosave-property.md) is **false**, then although the record is not modified automatically, the OnBeforeModifyRecord trigger is still called before the modification would have occurred.  
  
## See Also  
 [OnAfterModifyRecord Trigger](devenv-onaftermodifyrecord-trigger.md)   
 [OnAfterInsertRecord Trigger](devenv-onafterinsertrecord-trigger.md)   
 [OnBeforeInsertRecord Trigger](devenv-onbeforeinsertrecord-trigger.md)   
 [AutoReplace Property](../properties/devenv-autoreplace-property.md)   
 [AutoSave Property](../properties/devenv-autosave-property.md)   
 [AutoUpdate Property](../properties/devenv-autoupdate-property.md)  
 [Triggers](devenv-triggers.md)  
 [XMLport Triggers](devenv-xmlport-triggers.md)  