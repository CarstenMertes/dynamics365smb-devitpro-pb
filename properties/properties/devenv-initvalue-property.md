---
title: "InitValue Property"
ms.date: 10/01/2020
ms.suite: na
ms.topic: article
author: SusanneWindfeldPedersen
---

# InitValue Property

Sets the initial value of this field when a user creates a new record.  
  
## Applies to

- Fields

## Syntax

```AL
InitValue = 1;
```
 
## Remarks

This attribute is only important if you create the record in a window or by using the AL methods [CLEAR Method](../methods-auto/system/system-clear-joker-method.md), or [CLEARALL Method](../methods-auto/system/system-clearall-method.md). For example, this attribute is commonly used in Boolean fields when you want either **true** or **false** to be the default.  
  
## See Also

[Clear Method](../methods-auto/system/system-clear-joker-method.md)  
[ClearAll Method](../methods-auto/system/system-clearall-method.md)