---
title: "OnDelete (Table) Trigger"
description: "Runs when a user tries to delete a record."
ms.author: solsen
ms.custom: na
ms.date: 06/23/2021
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)

# OnDelete (Table) Trigger
> **Version**: _Available or changed with runtime version 1.0._

Runs when a user tries to delete a record.


## Syntax
```AL
trigger OnDelete()
begin
    ...
end;
```



[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  
 This trigger runs before the default delete behavior, which checks that the record exists before the deletion occurs. It runs automatically after the user chooses to delete a record in a page from the Web Client. If a user deletes a record using AL code, then the *RunTrigger* argument of [DELETE (Record) Method](../../methods-auto/record/record-delete-method.md) or [DELETEALL (Record) Method](../../methods-auto/record/record-deleteall-method.md) must be set to **true** for the OnDelete Trigger to run, or otherwise it will not. The record is not deleted if an error occurs in the trigger code.  

## See Also  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  
[OnDelete (Table Extension) Trigger](../tableextension/devenv-ondelete-tableextension-trigger.md)
