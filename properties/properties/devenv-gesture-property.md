---
title: "Gesture Property"
ms.date: 10/01/2020
ms.suite: na
ms.topic: article
ms.author: solsen
author: SusanneWindfeldPedersen
---

# Gesture Property

Specifies a gesture that runs the action on a device with a touch interface, such as the phone client.

## Applies to

*  Page Action controls

## Property values

The property has the following values:

|  Value  |  Description  |
|---------|---------------|
|**None** |No gesture for the action.|
|**LeftSwipe**|Swipe in from the right edge of the touch interface.  |
|**RightSwipe**|Swipe in from the left edge of the touch interface.  |

## Syntax

```AL
Gesture = None;
```

## Remarks

You typically use the Gesture property on list type pages for executing an action on items in a repeater control.

## See Also

[Implementation Tips for Gestures](devenv-implementation-tips-gestures-property.md)  
[Introducing the Dynamics 365 Business Central Mobile App](../devenv-introducing-business-central-mobile-app.md)   
<!-- [Adding Actions to Pages](../devenv-Adding-Actions-to-Pages.md) -->
