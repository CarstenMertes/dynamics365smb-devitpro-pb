---
title: "ClosingDates Property"
ms.date: 10/01/2020
ms.suite: na
ms.topic: article
ms.assetid: 9a98bc80-1b56-4f55-a31c-71a0609b9991
caps.latest.revision: 9
author: SusanneWindfeldPedersen
---

# ClosingDates Property

Sets a value that determines whether users can enter a closing date in this field. The default value is **false**.  
  
## Applies to  
  
- Table Fields  
- Page Fields  

## Property value

**True** if users can enter a closing date in the field, otherwise **false**. The default is **false**.

## Syntax

```AL
ClosingDates = true;
```

## Remarks  

All dates have a corresponding closing date. A closing date is a period following the given date, but before the next date. Closing dates are sorted immediately after the corresponding date but before the next date.  
  
 <!-- For fields, this property only applies to [Date and Time Methods](date-and-time-methods.md).  -->
  
## See Also  

[Date and Time Methods](../methods/devenv-date-and-time-methods.md)