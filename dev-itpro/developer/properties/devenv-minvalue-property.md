---
title: "MinValue Property"
description: "Sets the minimum numeric value for a field."
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
# MinValue Property
> **Version**: _Available or changed with runtime version 1.0._

Sets the minimum numeric value for a field.

## Applies to
-   Table Field
-   Page Field

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

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