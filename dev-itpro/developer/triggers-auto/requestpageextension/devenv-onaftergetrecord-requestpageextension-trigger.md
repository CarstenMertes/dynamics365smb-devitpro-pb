---
title: "OnAfterGetRecord (Request Page Extension) Trigger"
description: "Runs after a record is retrieved from a table but before it is displayed to the user."
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

# OnAfterGetRecord (Request Page Extension) Trigger
> **Version**: _Available or changed with runtime version 7.0._

Runs after a record is retrieved from a table but before it is displayed to the user.


## Syntax
```AL
trigger OnAfterGetRecord()
begin
    ...
end;
```



[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  

Use this trigger to calculate variables that depend on the current record. 

This trigger is independent of the currently selected record in the UI. When it gets raised depends on when the UI needs to load more data and the block size of the data read. So, for example, in a list page, where rows are read in larger blocks, then the `OnAfterGetRecord` trigger will be raised for each of the records read before the page is shown.

Within the trigger, the `Rec` variable will refer to the record just read.
  
If there is an error in the trigger code, then the page is closed.

## See Also  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  
[OnAfterGetRecord (Page) Trigger](../page/devenv-onaftergetrecord-page-trigger.md)  
[OnAfterGetRecord (Request Page) Trigger](../requestpage/devenv-onaftergetrecord-requestpage-trigger.md)  
[OnAfterGetRecord (Page Extension) Trigger](../pageextension/devenv-onaftergetrecord-pageextension-trigger.md)  
[OnAfterGetRecord (Report Data Item) Trigger](../reportdataitem/devenv-onaftergetrecord-reportdataitem-trigger.md)  
[OnAfterGetRecord (Xml Port Table Element) Trigger](../xmlporttableelement/devenv-onaftergetrecord-xmlporttableelement-trigger.md)
