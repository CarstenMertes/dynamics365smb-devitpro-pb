---
title: "SubType Property (BLOB)"
ms.custom: na
ms.date: 04/01/2021
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---

# SubType Property (BLOB)
> **Version**: _Available from runtime version 1.0._

Sets additional information about what will be contained in the field.  
  
## Applies to  

- BLOB fields  
  
## Property Value  
  
|**Value**                 |**Description**|  
|--------------------------|---------------|  
|**Bitmap**                |For storing bitmaps|  
|**Memo**                  |For storing memos|  
|**Json**|For storing Json data|  
|**User-Defined (default)**|For user defined information|  

 
## Syntax

```AL
SubType = Bitmap;
```

## See Also

[Properties](devenv-properties.md)   
[SubType Property (Codeunit)](devenv-subtype-codeunit-property.md)   