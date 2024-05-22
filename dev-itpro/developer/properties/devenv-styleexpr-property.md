---
title: "StyleExpr Property"
description: "Sets whether the format that is specified in the Style Property is applied to text in a field."
ms.author: solsen
ms.date: 05/14/2024
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# StyleExpr Property
> **Version**: _Available or changed with runtime version 1.0._

Sets whether the format that is specified in the Style Property is applied to text in a field. For fields in a CueGroup control, this property is used to configure the color of the color indicator on the cue.

This note pertains to backward compatibility only. If the property is set to Boolean true or false, it sets whether the format specified in the Style property is applied to text in a field.

## Applies to
-   Page Label
-   Page Field

[//]: # (IMPORTANT: END>DO_NOT_EDIT)


## Remarks  

> [!NOTE]  
> The information in this topic is mainly applicable to formatting the text of page fields. 

<!-- For information about how to use the **StyleExpr** property for configuring Cues, see [How to: Set Up Colored Indicators on Cues by Using the Style and StyleExpr Property](devenv-How-to-Set-Up-Colored-Indicators-on-Cues-by-Using-the-Style-and-StyleExpr-Property.md).  -->

You can use a conditional setting of styles by inserting the conditional code in, for example, the [OnAfterGetRecord Trigger](../triggers-auto/page/devenv-onaftergetrecord-page-trigger.md). Remember to cover all cases in else branches to avoid incorrect styles. For example: 

```al
if (MyField = 'abc') 
    then 
        MyStyleVar := 'Ambiguous' 
    else 
        MyStyleVar := 'Favorable'
```

> [!NOTE]  
> To use a variable for the **StyleExpr** property, it must be set as a global page variable.  

## See Also

[Properties](devenv-properties.md)  