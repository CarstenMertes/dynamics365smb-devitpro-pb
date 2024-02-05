---
title: "Numeric Property"
description: "Sets a value that requires that users enter only numbers in the field."
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
# Numeric Property
> **Version**: _Available or changed with runtime version 1.0._

Sets a value that requires that users enter only numbers in the field.

## Applies to
-   Table Field
-   Page Field

[//]: # (IMPORTANT: END>DO_NOT_EDIT)


## Syntax

```AL
Numeric = true;
```
  
## Remarks  

This setting is checked during validation. Validation occurs only if the field or control value is updated through the UI, for example, if a value is updated on a page or if a field is updated in a table directly. If a field is updated through application code, then the **Numeric** property is not validated.  
  
## See Also  

[MinValue Property](devenv-minvalue-property.md)  
[MaxValue Property](devenv-maxvalue-property.md)  
[Properties](devenv-properties.md)
