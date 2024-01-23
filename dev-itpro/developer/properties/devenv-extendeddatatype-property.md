---
title: "ExtendedDatatype Property"
description: "Sets the extended data type of a control."
ms.author: solsen
ms.custom: na
ms.date: 11/24/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# ExtendedDatatype Property
> **Version**: _Available or changed with runtime version 1.0._

Sets the extended data type of a control.

## Applies to
-   Table Field
-   Page Field

## Property Value

|Value|Available or changed with|Description|
|-----------|-----------|---------------------------------------|
|**None**|runtime version 1.0|Default value. No conversion is applied.|
|**PhoneNo**|runtime version 1.0|The client handles the field as a phone number and will display this as hyperlinked whenever the field is not editable. Activating the hyperlink will launch the default dialing app on your device.|
|**URL**|runtime version 1.0|The client handles the field as a URL and the text will be displayed as hyperlinked whenever the field is not editable. Activating the hyperlink will open the URL using the default browser on your device.|
|**EMail**|runtime version 1.0|The client handles the field as an email address and will display this as hyperlinked whenever the field is not editable. Activating the hyperlink will launch the default mail app on your device.|
|**Ratio**|runtime version 1.0|The text is handled as a progress bar. This is not supported on the Web client.|
|**Masked**|runtime version 1.0|Displays the value as dots. This will only have effect on fields, where the user can enter and display textual data (including numbers, time, date etc.)|
|**Person**|runtime version 1.0|The client handles the field as media representing a person and will display this in the signature rounded styling. When the media field is empty, a silhouette of a person is shown.|
|**Barcode**|runtime version 12.0|The phone and tablet clients handle the field as a code and will provide the option to set the field value using a barcode scanner.|
|**RichContent**|runtime version 12.0|The client handles the field as a rich text field, which allows for styling and formatting. To enable a rich text field, the field must have the MultiLine property set to `true` and must reside alone within a FastTab group.|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)


## Syntax

```AL
ExtendedDatatype = EMail;
```
 
## Remarks

The property affects the layout and behavior of controls on a page. Use this, for example, to display a field as an email address.

By applying special meaning or semantics to a field, the value of the table field is converted to a text field of the new data type that may apply special validation, a different way of displaying the value or interacting with the field.

The value of this property on a page control overrides the same property on a table field.

With [!INCLUDE [prod_short](../includes/prod_short.md)] 2023 release wave 2, you can use the `RichContent` option to enable a rich text field. To enable a rich text field, the field must have the [Multiline property](devenv-multiline-property.md) set to `true` and it must reside alone within a FastTab group. For an example of creating a rich text editor, see [Creating a rich text editor](../devenv-richtext-content-controls.md).

## See Also

[Properties](devenv-properties.md)  
[Creating a rich text editor](../devenv-richtext-content-controls.md)