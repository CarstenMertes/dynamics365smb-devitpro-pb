---
title: "OnBeforeDelete Trigger"
description: "OnBeforeDelete trigger in AL for Business Central."
ms.date: 04/01/2021
ms.reviewer: solsen
ms.topic: reference
ms.author: t-blrobl
author: blrobl
---

# OnBeforeDelete Trigger
Runs when the user tries to delete a record. 

## Applies to  
- Table extensions 
  
## Remarks  
 This trigger runs before the default delete behavior is executed on a record to be deleted. It runs automatically after the user chooses to delete a record in a page from the Web client. The record is not deleted if an error occurs in the trigger code. 

## See Also  
 [Triggers](devenv-triggers.md)  
 [Table and Field Triggers](devenv-table-and-field-triggers.md)   
 [OnAfterDelete Trigger](devenv-onafterdelete-trigger.md)    
