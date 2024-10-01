---
title: "OnRename Trigger"
description: "OnRename trigger in AL for Business Central."
ms.date: 04/01/2021
ms.topic: reference
author: SusanneWindfeldPedersen
---

# OnRename Trigger
Runs when a user tries to rename a record.  
  
## Applies to  
- Tables  
- Table extensions
  
## Remarks  
When you rename a record in one location, it is updated in all other locations. It runs automatically when the user changes a record's primary key field in a page from the Web Client.  The OnRename trigger runs after field validation and before the default renaming behavior, which checks that the new name does not correspond to an already existing record before the rename occurs. The record is not renamed if an error occurs in the trigger code.  
  
## See Also  
 [Triggers](devenv-triggers.md)  
 [Table and Field Triggers](devenv-table-and-field-triggers.md)  