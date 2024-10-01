---
title: "OnDeleteRecord (Request Page Extension) trigger"
description: "Runs before a record is deleted from the table."
ms.author: solsen
ms.date: 08/26/2024
ms.topic: reference
author: SusanneWindfeldPedersen
ms.reviewer: solsen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)

# OnDeleteRecord (Request Page Extension) trigger
> **Version**: _Available or changed with runtime version 7.0._

Runs before a record is deleted from the table.


## Syntax
```AL
trigger OnDeleteRecord(): Ok
begin
    ...
end;
```


## Return Value

*Ok*  
&emsp;Type: [Boolean](../../methods-auto/boolean/boolean-data-type.md)  
**true** if the record was deleted, otherwise, **false**. The return value is checked after each call. The default value is **true**.  

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  

The action is canceled but the page is not closed if an error occurs in the trigger code. You can use this trigger to write to the database.  

## Related information  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  
[OnDeleteRecord (Page) Trigger](../page/devenv-ondeleterecord-page-trigger.md)  
[OnDeleteRecord (Request Page) Trigger](../requestpage/devenv-ondeleterecord-requestpage-trigger.md)  
[OnDeleteRecord (Page Extension) Trigger](../pageextension/devenv-ondeleterecord-pageextension-trigger.md)  
