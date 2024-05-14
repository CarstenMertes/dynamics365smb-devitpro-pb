---
title: "PasteIsValid Property"
ms.date: 10/01/2020
ms.suite: na
ms.topic: article
ms.assetid: 7f3e261c-65ba-4adc-9fba-344a6eca8146
caps.latest.revision: 6
author: SusanneWindfeldPedersen
---

# PasteIsValid Property

Sets whether inserting records into this table using the paste command is enabled.  
  
## Applies to  

- Tables  
  
## Property Value  

**True** if you want to allow insert by pasting; otherwise, **false**. The default value is **true**.  
 
## Syntax

```AL
PasteIsValid = false;
```

## Remarks

If records are usually inserted in the table through an external code unit function, set the PasteIsValid property equal to **false**.  
  
The [OnInsert Trigger](../triggers/devenv-oninsert-trigger.md) of the table is executed when a record is inserted by pasting.  
  
## See Also  

[OnInsert Trigger](../triggers/devenv-oninsert-trigger.md)
[Properties](devenv-properties.md)