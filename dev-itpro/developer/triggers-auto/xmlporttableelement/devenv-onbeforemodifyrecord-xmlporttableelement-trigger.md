---
title: "OnBeforeModifyRecord (Xml Port Table Element) Trigger"
description: "Runs after a record is read from the input stream and before the existing record in the database is modified."
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

# OnBeforeModifyRecord (Xml Port Table Element) Trigger
> **Version**: _Available or changed with runtime version 1.0._

Runs after a record is read from the input stream and before the existing record in the database is modified.


## Syntax
```AL
trigger OnBeforeModifyRecord()
begin
    ...
end;
```



[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  
 This trigger is used when you import data from an XMLport and then update an existing record in a table with the data from the XMLport.  
  
 If the [AutoSave Property](../../properties/devenv-autosave-property.md) is **false**, then although the record is not modified automatically, the **OnBeforeModifyRecord** trigger is still called before the modification would have occurred.  

## See Also  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  
