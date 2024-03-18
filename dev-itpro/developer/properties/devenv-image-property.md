---
title: "Image Property"
description: "Specifies the icon that you want to associate with a field in a CueGroup control."
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
# Image Property
> **Version**: _Available or changed with runtime version 1.0._

Specifies the icon that you want to associate with a field in a CueGroup control.

## Applies to
-   Page Field
-   Page Action
-   Page Action Group

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

  > [!NOTE]  
  > You can only use images on fields that have an integer data type.

## Syntax

```AL
Image = Report;
```

## Remarks

On **RoleCenter** type pages, the image property doesn't apply to actions that are set up in the navigation bar or top-level actions in the action bar. These actions can't be assigned in icon, or if they have icon by default, the icon can't be changed. The property only applies to subgroups and child actions in the action bar.

[!INCLUDE[available_icons](../includes/include-available-icons.md)]

## See Also

[Properties](devenv-properties.md)   
[Available icons](https://aka.ms/bcicons)   