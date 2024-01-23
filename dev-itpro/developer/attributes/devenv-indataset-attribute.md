---
title: "InDataSet Attribute"
description: "Sets whether the AL variable's value is included in the dataset."
ms.author: solsen
ms.custom: na
ms.date: 08/02/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)

# InDataSet Attribute
> **Version**: _Available or changed with runtime version 1.0 until version 11.0 where it was deprecated for the following reason: "The InDataset attribute is unused."_

Sets whether the AL variable's value is included in the dataset.


## Applies To

- Variable


## Syntax

```AL
[InDataSet]
```

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Example

```al
var
    [InDataSet]
    StyleIsStrong: Boolean;
    [InDataSet]
    NameIndent: Integer;
```

## Remarks

The **InDataSet** attribute is defined on variables of the type [Boolean](../methods-auto/boolean/boolean-data-type.md) or [Integer](../methods-auto/integer/integer-data-type.md) on pages.  

You must define this attribute on a variable if it's used as the value of the [Editable Property](../properties/devenv-editable-property.md), [Enabled Property](../properties/devenv-enabled-property.md), [Visible Property](../properties/devenv-visible-property.md) and [StyleExpr Property](../properties/devenv-styleexpr-property.md).  

> [!NOTE]
> This attribute is obsolete. It no longer works and isn't required to include the AL variable's value in the dataset.

## See Also

[AL Method Reference](../methods-auto/library.md)  
[StyleExpr Property](../properties/devenv-styleexpr-property.md)  
[Editable Property](../properties/devenv-editable-property.md)  
[Enabled Property](../properties/devenv-enabled-property.md)  
[Visible Property](../properties/devenv-visible-property.md)