---
title: "HideValue Property"
description: "Sets whether to show or hide a value for the user based on an expression."
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
# HideValue Property
> **Version**: _Available or changed with runtime version 3.2._

Sets whether to show or hide a value for the user based on an expression.

## Applies to
-   Page Label
-   Page Field

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Property Values  

**True** if the value is hidden; otherwise, **false**. The default is **false**.  

## Syntax

```AL
HideValue = true;
```
  
## Remarks

- `HideValue` is useful for choosing to hide a value based on some conditions; such as the value of another field.
 
> [!IMPORTANT]  
> The field value is shown in the UI as an empty space. If the field happens to also define a drilldown control; the space may show as underlined. This is intended for UI clarity, *not security*. We advise against using this for security by obscurity: the underlying value will still be visible to the user in certain cases such as page inspector, table viewer, etc.

- Accessing the same table from other pages, from OData APIs or other integrating apps may reveal the value. These must each implement their own mechanisms to hide the value under the same conditions. For example, the Excel AddIn, Power Apps, Power BI, and cards displayed by the Teams app do not respect this property.

## See Also  

[Properties](devenv-properties.md)