---
title: "OnAfterModify Trigger"
description: "OnAfterModify trigger in AL for Business Central."
ms.date: 04/01/2021
ms.reviewer: solsen
ms.topic: reference
ms.author: t-blrobl
author: blrobl
---

# OnAfterModify Trigger
Runs when a user modifies an existing record in a table.  
  
## Applies to  
- Table extensions
  
## Remarks  
 This trigger is run after the default modify behavior, which checks that all the fields of a record are valid before the modification occurs. It runs automatically when the user changes at least one field (different from the primary key field) of a record in a page from the Web Client. If an error occurs in the trigger code, the record changes are canceled.  
  
## See Also  
 [Triggers](devenv-triggers.md)  
 [Table and Field Triggers](devenv-table-and-field-triggers.md)  
 [OnBeforeModify Trigger](devenv-onbeforemodify-trigger.md)
