---
title: "PageStyle system option"
description: "Represents the different kinds of styles that can be applied to page controls."
ms.author: solsen
ms.date: 08/08/2025
ms.topic: reference
author: SusanneWindfeldPedersen
ms.reviewer: solsen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# PageStyle option type
> **Version**: _Available or changed with runtime version 14.0._

Represents the different kinds of styles that can be applied to page controls.

## Members
|  Member  |  Description  |
|----------------|---------------|
|None|None|
|Standard|Standard|
|StandardAccent|Blue|
|Strong|Bold|
|StrongAccent|Blue + Bold|
|Attention|Red + Italic|
|AttentionAccent|Blue + Italic|
|Favorable|Bold + Green|
|Unfavorable|Bold + Italic + Red|
|Ambiguous|Yellow|
|Subordinate|Grey|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Example

The `PageStyle` option type can be used to get the valid values for [StyleExpr](../../properties/devenv-styleexpr-property.md), which is set on page controls.

```AL
layout
{
    area(Content)
    {
        field(Name; rec.Name)
        {
            StyleExpr = nameStyle;
        }
    }
}

var nameStyle : Text;

local procedure ChangeNameStyle(newPageStyle : PageStyle)
begin
    nameStyle := format(newPageStyle);
end;
```

## Related information  
[Getting Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  