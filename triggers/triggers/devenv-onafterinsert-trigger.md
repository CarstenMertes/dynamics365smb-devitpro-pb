---
title: "OnAfterInsert Trigger"
description: "OnAfterInsert trigger in AL for Business Central."
ms.date: 04/01/2021
ms.reviewer: solsen
ms.topic: reference
ms.author: t-blrobl
author: blrobl
---

# OnAfterInsert Trigger
Runs when a user inserts a new record into the table.  
  
## Applies to  
- Table extensions
  
## Remarks  
 This trigger is run after default insert behavior, which checks that the record to be inserted does not already exist before the insertion occurs. It runs automatically after the user chooses to insert a new record in a page from the Web Client. The new record is not inserted if an error occurs in the trigger code.  
  
## See Also  
 [Triggers](devenv-triggers.md)   
 [Table and Field Triggers](devenv-table-and-field-triggers.md)  
 [OnBeforeInsert Trigger](devenv-onbeforeinsert-trigger.md)