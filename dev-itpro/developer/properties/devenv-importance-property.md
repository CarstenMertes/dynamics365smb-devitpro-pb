---
title: "Importance Property"
description: "Sets the amount of information that is visible in a window or dialog box."
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
# Importance Property
> **Version**: _Available or changed with runtime version 3.2._

Sets the amount of information that is visible in a window or dialog box.

## Applies to
-   Page Label
-   Page Field

## Property Value

|Value|Available or changed with|Description|
|-----------|-----------|---------------------------------------|
|**Standard**|runtime version 1.0|Displays the field on the page by default.|
|**Promoted**|runtime version 1.0|Displays the field on the page and also in the header of the FastTab when the FastTab is collapsed.|
|**Additional**|runtime version 1.0|Hides the field by default. On a FastTab, to show the field, a user can choose **Show more** to display the field.|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Syntax

```AL
Importance = Additional;
```
  
## Remarks

You use this property to control the amount of information that is visible on a page. It is useful on pages that have a large number of fields, where you can display the most important fields by default, but users have the option to show more as needed.  

As a developer, the **Importance** property can also be set also by Use Designer (see [Use Designer](../devenv-inclient-designer.md)). In the client, users can change the setting for their workspace by using personalization (see [Personalizing Your Workspace](/dynamics365/business-central/ui-personalization-user).

## See Also

[Properties](devenv-properties.md)