---
title: "ShortcutKey Property"
description: "Sets a shortcut key for selecting a menu item."
ms.author: solsen
ms.custom: na
ms.date: 12/15/2022
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# ShortcutKey Property
> **Version**: _Available or changed with runtime version 1.0._

Sets a shortcut key for selecting a menu item.

## Applies to
-   Page Action
-   Page Custom Action

[//]: # (IMPORTANT: END>DO_NOT_EDIT)


## Syntax

```AL
ShortCutKey = 'Shift+Ctrl+D';
```

## Remarks

Pressing the key that you designate with this property provides the same result as selecting the action.  

> [!NOTE]  
> Actions are used in different contexts to drive different experiences in the user interface. Be aware that keyboard shortcuts are not supported across all contexts. For example, the `ShortcutKey` property is not supported for actions defined in `area(sections)` or `area(embedding)`.

Some shortcut keys have default assignments. Don't reuse shortcut keys that are already assigned. For a list of these shortcuts, see [Keyboard Shortcuts for the Dynamics 365 Business Central Web Client](/dynamics365/business-central/keyboard-shortcuts). 

> [!NOTE]  
> The shortcut keys that you set with this property have precedence over the default shortcut keys of the web browser that you are using and that they will override their behavior.

For more information, see [Adding Actions to a Page](../devenv-adding-actions-to-a-page.md).
  
## See Also

[Properties](devenv-properties.md)
