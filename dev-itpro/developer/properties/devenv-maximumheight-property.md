---
title: "MaximumHeight Property"
description: "Specifies the maximum height that the control add-in can be stretched to."
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
# MaximumHeight Property
> **Version**: _Available or changed with runtime version 1.0._

Specifies the maximum height that the control add-in can be stretched to. This setting only applies if the VerticalStretch setting is specified.

## Applies to
-   Control Add In

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

  
## Value Type 
  
- Integer 

## Property Values

The default is the integer’s maximum value. If [VerticalStretch](devenv-verticalstretch-property.md) is **true** but MaximumHeight is not set, the control add-in can expand indefinitely.

## Dependent Property

This setting only applies if [VerticalStretch](devenv-verticalstretch-property.md) is set to **true**.

## Remarks

Use this property when the visual content of the add-in is no longer usable or no longer visually appealing beyond a certain size.

## Example

```AL
RequestedHeight = 300;
VerticalStretch = true;
MaximumHeight = 500;
```


## See Also

[Control Add-In Object](../devenv-control-addin-object.md)   
 