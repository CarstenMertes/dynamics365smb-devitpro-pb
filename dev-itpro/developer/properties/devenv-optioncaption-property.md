---
title: "OptionCaption Property"
description: "Sets the string string options that are displayed to the user."
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
# OptionCaption Property
> **Version**: _Available or changed with runtime version 1.0._

Sets the string string options that are displayed to the user.

## Applies to
-   Table Field
-   Page Field
-   Report Column

[//]: # (IMPORTANT: END>DO_NOT_EDIT)


## Syntax

```AL
field(1300; "Payment Prediction"; Option)
{
    OptionMembers = " ",Late,"On-Time";
    OptionCaption = ' ,Late,On-Time';
}
```

```AL
field(1301; "Prediction Confidence"; Option)
{
    OptionMembers = " ",Low,Medium,High;
    OptionCaption = ' ,Low,Medium,High';
}
```

## Remarks

**OptionCaption** sets the text used to show the option values available for a variable or a field on a page or report. The [OptionString Property](./devenv-optionmembers-field-property.md) contains the set of values that are acceptable choices. If you have set the [OptionCaptionML Property](devenv-optioncaptionml-property.md), this overrides the OptionCaption setting.  
  
## See Also  

[OptionString Property](./devenv-optionmembers-field-property.md)  
[OptionCaptionML Property](devenv-optioncaptionml-property.md)