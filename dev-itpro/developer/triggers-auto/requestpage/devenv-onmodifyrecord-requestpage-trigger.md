---
title: "OnModifyRecord (Request Page) Trigger"
description: "Runs before a record is modified in the table."
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

# OnModifyRecord (Request Page) Trigger
> **Version**: _Available or changed with runtime version 1.0._

Runs before a record is modified in the table.


## Syntax
```AL
trigger OnModifyRecord(): Ok
begin
    ...
end;
```


## Return Value

*Ok*  
&emsp;Type: [Boolean](../../methods-auto/boolean/boolean-data-type.md)  
**true** if the record was modified, otherwise **false**. The return value is checked after each call. The default value is **true**.  

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  

If an error occurs in the trigger code, the action is canceled, but the page is not closed.  
  
You can write to the database using this trigger.  

## See Also  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  
[OnModifyRecord (Page) Trigger](../page/devenv-onmodifyrecord-page-trigger.md)  
[OnModifyRecord (Request Page Extension) Trigger](../requestpageextension/devenv-onmodifyrecord-requestpageextension-trigger.md)  
[OnModifyRecord (Page Extension) Trigger](../pageextension/devenv-onmodifyrecord-pageextension-trigger.md)
