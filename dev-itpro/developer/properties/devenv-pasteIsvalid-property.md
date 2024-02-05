---
title: "PasteIsValid Property"
description: "Sets whether inserting records into this table using the paste command is enabled."
ms.author: solsen
ms.custom: na
ms.date: 06/15/2022
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# PasteIsValid Property
> **Version**: _Available or changed with runtime version 1.0._

Sets whether inserting records into this table using the paste command is enabled.

## Applies to
-   Table

[//]: # (IMPORTANT: END>DO_NOT_EDIT)


## Property Value  

**True** if you want to allow insert by pasting; otherwise, **false**. The default value is **true**.  
 
## Syntax

```AL
PasteIsValid = false;
```

## Remarks

If records are usually inserted in the table through an external code unit function, set the PasteIsValid property equal to **false**.  
  
The [OnInsert Trigger](../triggers-auto/table/devenv-oninsert-table-trigger.md) of the table is executed when a record is inserted by pasting.  
  
## See Also  

[OnInsert Trigger](../triggers-auto/table/devenv-oninsert-table-trigger.md)
[Properties](devenv-properties.md)