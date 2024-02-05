---
title: "OptionMembers Property (Table field)"
ms.custom: na
ms.date: 12/29/2022
ms.reviewer: na
ms.topic: reference
ms.author: solsen
---

# OptionMembers Property (Table field)
> **Version**: _Available from runtime version 1.0._

Sets the list of options that are available in the table field that is currently selected. 
  
## Applies to  
  
- Table fields  

## Example

In the code snippet below, you can see how the property is set.

```AL
field(2; OptionField; option)
{
    OptionMembers = "Option with ", "spaces and ", "other symbols!";
}
```

Setting the `OptionMembers` property is necessary to enable the `OptionCaptionML` property. For more information, see [OptionCaptionML Property](devenv-optioncaptionml-property.md).

## See Also

[Properties](devenv-properties.md)  
[Report Object](../devenv-report-object.md)     
[Report Properties](devenv-report-properties.md)   
[OptionMembers Property (Report)](devenv-optionmembers-report-property.md)