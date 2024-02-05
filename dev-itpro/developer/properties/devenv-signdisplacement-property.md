---
title: "SignDisplacement Property"
description: "Sets a value to shift negative values to the right for display purposes only."
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
# SignDisplacement Property
> **Version**: _Available or changed with runtime version 1.0._

Sets a value to shift negative values to the right for display purposes only. You can shift negative values in increments of 1/100 of a millimeter.

## Applies to
-   Table Field
-   Page Field

[//]: # (IMPORTANT: END>DO_NOT_EDIT)


## Syntax

```AL
SignDisplacement = 600; 
```
  
## Remarks  

For example, if you enter 600 (6 millimeters) you would see a result similar to:  
  
(+)999888777  
  
(+)123456789  
  
(-) 123456789  
  
(-) 999888777  
  
(+)987654321  
  
## See Also  

[Properties](devenv-properties.md)