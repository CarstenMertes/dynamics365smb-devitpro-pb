---
title: "BlankNumbers Property"
ms.date: 10/01/2020
ms.suite: na
ms.topic: article
ms.assetid: cd877cdb-059d-4f88-a071-cbb1b99b4eb0
caps.latest.revision: 8
author: SusanneWindfeldPedersen
---

# BlankNumbers Property
Indicates whether the system will clear a range of numbers as it formats them.  
  
## Applies to  
  
- Page Fields  
  
## Property Value  
  
|**Value**|**Description**|  
|---------------|---------------------|  
|**DontBlank (default)**|Not clear any numbers|  
|**BlankNeg**|Clear negative numbers|  
|**BlankNegAndZero**|Clear negative numbers and zero|  
|**BlankZero**|Clear numbers equal to zero|  
|**BlankZeroAndPos**|Clear positive numbers and zero|  
|**BlankPos**|Clear positive numbers|  

## Syntax  
```AL
BlankNumbers = BlankNegAndZero;
```

## See Also  
 [BlankZero Property](devenv-blankzero-property.md)