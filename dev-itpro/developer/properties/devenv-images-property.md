---
title: "Images Property"
description: "Specifies the list of images to include in the control add-in."
ms.author: solsen
ms.custom: na
ms.date: 11/15/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Images Property
> **Version**: _Available or changed with runtime version 1.0._

Specifies the list of images to include in the control add-in.

## Applies to
-   Control Add In

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Property Values

A list of comma-separated strings that represents paths to image files. The default is blank, with no images being used by the control add-in. 

You can specify multiple files within the same path string by using a combination of a valid literal path and wildcard characters (* and ?). However, it doesn't support regular expressions.

## Remarks

The Images property specifies image resources that are referenced by the control add-in scripts. Any specified images must be of a supported web format and extension, such as .PNG or .GIF. 

Images can be either external resources referenced using a URL or can be embedded within the extension. Embedded images must be added to the extension project folder in Visual Studio Code and referenced using a relative path. At runtime, the path to an embedded can be obtained using the [GetImageResource method](../methods/devenv-getimageresource-method.md) method. Unlike scripts and stylesheets, images are loaded on demand when they're first used in code. Since images are stored in the application after the extension is deployed, it's recommended to keep the number of image files and combined image size to a minimum. 

## Example

```AL
Images = 'https://fabrikam.com/banner.png',
              'images/map.png',
              'images/*.png';
```

## See Also  

[Control Add-In Object](../devenv-control-addin-object.md)   