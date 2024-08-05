---
title: "ClearOnLookup Property"
ms.date: 10/01/2020
ms.suite: na
ms.topic: article
ms.assetid: a627fc31-d854-4204-8b75-20152d397ca5
caps.latest.revision: 9
author: SusanneWindfeldPedersen
---

 

# ClearOnLookup Property
Sets a value that determines whether the current contents of the field are deleted before the value that is selected via the lookup is added.  
  
## Applies to  
  
- Fields  

## Property Value  

**True** if current contents of the field are replaced; otherwise, **false** if the contents are pasted. The default value is **true** for all fields except FlowFilters fields.  

## Syntax

```AL
ClearOnLookup = true;
```
  
## See Also

[FlowFilter Overview](../devenv-flowfilter-overview.md)