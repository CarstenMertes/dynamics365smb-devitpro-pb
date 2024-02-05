---
title: "Style Property"
description: "Sets a value that determines how text in a field on a page is formatted."
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
# Style Property
> **Version**: _Available or changed with runtime version 1.0._

Sets a value that determines how text in a field on a page is formatted. For fields that are included in a CueGroup, this property sets the value of the color indicator on the cue.

## Applies to
-   Page Label
-   Page Field

## Property Value

|Value|Available or changed with|Description|
|-----------|-----------|---------------------------------------|
|**None**|runtime version 1.0|None|
|**Standard**|runtime version 1.0|Standard|
|**StandardAccent**|runtime version 1.0|Blue|
|**Strong**|runtime version 1.0|Bold|
|**StrongAccent**|runtime version 1.0|Blue + Bold|
|**Attention**|runtime version 1.0|Red + Italic|
|**AttentionAccent**|runtime version 1.0|Blue + Italic|
|**Favorable**|runtime version 1.0|Bold + Green|
|**Unfavorable**|runtime version 1.0|Bold + Italic + Red|
|**Ambiguous**|runtime version 1.0|Yellow|
|**Subordinate**|runtime version 1.0|Grey|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)


## Remarks  

> [!NOTE]  
> This information in this topic mainly pertains to formatting the text on page fields. <!-- For information about how to use the **Style** property for configuring Cues, see [How to: Set Up Colored Indicators on Cues by Using the Style and StyleExpr Property](devenv-How-to-Set-Up-Colored-Indicators-on-Cues-by-Using-the-Style-and-StyleExpr-Property.md).  -->

The **Style** property works together with the [StyleExpr Property](devenv-styleexpr-property.md) value to determine whether the field is formatted. If the [StyleExpr Property](devenv-styleexpr-property.md) evaluates to **true**, then the value of the field is formatted as specified by the **Style** property.  

By default, the **Style** property is not set.  

This property is not supported if one of the following data types is used for the SourceExpr of the field:  

- Code  
- Boolean  
- Binary  
- BLOB  
- GUID  
- RecordID  

On pages, you use the **Style** property for group, part, field, and action controls. You can change the formatting of a control either statically by setting the [StyleExpr Property](devenv-styleexpr-property.md) to **true** or **false**, or dynamically by using a Boolean variable or a Boolean field on the page. The Boolean field on the page can be either a true/false Boolean or a Boolean expression, such as “Credit Limit > Sales YTD”.  

## Example

The following code sample shows how to make the text of the field control `"Code"` bold using the **Style** property. The text will be formatted only if the Boolean variable `Emphasize` evaluates to **true**.

```AL
field("Code"; Code)
    {
        Style = Strong;
        StyleExpr = Emphasize;
    }
```

## See Also  
<!-- [How to: Style Field Text on a Page](../devenv-How-to-Style-Field-Text-on-a-Page.md)   -->
[Properties](devenv-properties.md)
