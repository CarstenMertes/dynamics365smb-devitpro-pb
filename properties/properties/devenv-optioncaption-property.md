---
title: "OptionCaption Property"
ms.date: 10/01/2020
ms.suite: na
ms.topic: article
author: SusanneWindfeldPedersen
---

# OptionCaption Property

Sets the text string options that are displayed to the user.  
  
## Applies to  
  
- Pages  
- Reports  
- Variables  

## Parameters

*Locked*  
&emsp;Type: [Boolean](../methods-auto/boolean/boolean-data-type.md)  
If `true` the OptionCaption is locked and should not be translated.  

*Comment*  
&emsp;Type: [Text](../methods-auto/text/text-data-type.md)  
Descriptive text for the OptionCaption, for example, with regards to translation.

*MaxLength*  
&emsp;Type: [Integer](../methods-auto/integer/integer-data-type.md)  
Sets the maximum length of the specific OptionCaption property value.

## Syntax

```AL
field(1300; "Payment Prediction"; Option)
{
    OptionMembers = " ",Late,"On-Time";
    OptionCaption = ' ,Late,On-Time';
}
```

Or, with parameters:

```AL
field(1301; "Prediction Confidence"; Option)
{
    OptionMembers = " ",Low,Medium,High;
    OptionCaption = ' ,Low,Medium,High', Locked = true, Comment = 'Do not translate, MaxLength = 100;
}
```

## Remarks

**OptionCaption** sets the text used to show the option values available for a variable or a field on a page or report. The [OptionString Property](devenv-optionstring-property.md) contains the set of values that are acceptable choices. If you have set the [OptionCaptionML Property](devenv-optioncaptionml-property.md), this overrides the OptionCaption setting.  
  
## See Also  

[OptionString Property](devenv-optionstring-property.md)   
[OptionCaptionML Property](devenv-optioncaptionml-property.md)