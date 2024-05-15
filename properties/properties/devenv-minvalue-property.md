---
title: "MinValue Property"
ms.date: 10/01/2020
ms.suite: na
ms.topic: article
ms.assetid: 531a1e04-cd17-4128-a230-fbaa6ba33b65
caps.latest.revision: 9
author: SusanneWindfeldPedersen
---

# MinValue Property

Sets the minimum value for a field.  
  
## Applies to  
  
- Page Fields  
  
## Property Value  
  
|**Value**|**Description**|  
|---------|---------------|  
|**0**|Integers|  
|**0.0**|Decimals|  
|**January 1, 0**|Dates|  
|**00:00:00**|Time|  

## Syntax

```AL
MinValue = 0;
```
 
## Remarks

The field setting is checked during validation. Validation occurs only if the field or control value is updated through the UI, for example, if a value is updated on a page or if a field is updated in a table directly. If a field is updated through application code, then the **MinValue** property is not validated.  
  
## See Also  

[MaxValue Property](devenv-maxvalue-property.md)   
[NotBlank Property](devenv-notblank-property.md)   
[Numeric Property](devenv-numeric-property.md)