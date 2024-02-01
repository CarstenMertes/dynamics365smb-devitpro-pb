---
title: "UpdatePropagation Property"
description: "Sets a value that specifies what happens when a main page with a subpage is updated."
ms.author: solsen
ms.custom: na
ms.date: 12/08/2022
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# UpdatePropagation Property
> **Version**: _Available or changed with runtime version 1.0._

Sets a value that specifies what happens when a main page with a subpage is updated. The UpdatePropagation property is available on part controls and has two options; Subpage and Both. If UpdatePropagation is set to Subpage, an update action will update the subpage only. If UpdatePropagation is set to Both, an update action will update both the main page and the subpage. This is useful if a value on the subpage changes, and you want a main page total to be refreshed automatically.

## Applies to
-   Page Part
-   Page System Part
-   Page Chart Part

## Property Value

|Value|Available or changed with|Description|
|-----------|-----------|---------------------------------------|
|**SubPart**|runtime version 1.0|An update action will update the subpage only|
|**Both**|runtime version 1.0|An update action will update both the main page and the subpage|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)


## Syntax

```AL
 UpdatePropagation = Both;
```
 
## Remarks

Use the **UpdatePropagation** property to update a main page total, when the amount on the subpage lines is updated. Add a `CurrPage.Update();` call, for example, in the OnValidate trigger on the subpage to have the **UpdatePropagation** property take effect.

## See Also

[Properties](devenv-properties.md) 
