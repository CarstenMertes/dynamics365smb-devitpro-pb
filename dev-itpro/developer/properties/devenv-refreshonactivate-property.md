---
title: "RefreshOnActivate Property"
description: "Set this property on pages where you want to refresh the data when the user navigates back from another page."
ms.author: solsen
ms.date: 02/26/2024
ms.tgt_pltfrm: na
ms.topic: reference
author: SusanneWindfeldPedersen
ms.reviewer: solsen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# RefreshOnActivate Property
> **Version**: _Available or changed with runtime version 1.0._

Set this property on pages where you want to refresh the data when the user navigates back from another page.

## Applies to
-   Page

[//]: # (IMPORTANT: END>DO_NOT_EDIT)


## Syntax

```AL
RefreshOnActivate = true;
```
 
## Remarks

On RoleCenters, modifying data in one part will automatically refresh data in any other parts which have the RefreshOnActivate property set to **true**.

## See Also  

[Properties](devenv-properties.md)  
[Page Properties](./devenv-properties.md)