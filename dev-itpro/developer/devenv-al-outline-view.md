---
title: AL outline view
description: Description of the outline view in Visual Studio Code.
author: SusanneWindfeldPedersen
ms.date: 06/13/2025
ms.topic: concept-article
ms.author: solsen
ms.collection: get-started
ms.reviewer: solsen
---

# AL outline view

Working with the [!INCLUDE[d365al_ext_md](../includes/d365al_ext_md.md)], you have access to the **Outline** view. The **Outline** view is a separate section in the lower left corner, right under the **Explorer** view.

The **Outline** view is enabled by default and shows the symbol tree of the currently active cursor, it also allows you to filter as you type. Double-clicking on any node makes your cursor jump to the selected definition or keyword. The **Outline** view will also display any errors in your project for an easy review.

![Outline view.](media/outlineview.png "Outline view in Visual Studio Code")

You manage the look and feel of the **Outline** view by defining settings that are all enabled by default. To modify settings, select <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>, and then choose **Preferences: Open Settings (UI)** for workspace settings, or choose **Preferences: Open User Settings** for user settings. Under **Extensions**, and **AL Language extension configuration** you'll find the settings that are available for the AL Language extension for the `settings.json` file.

- `outline.collapsItems` - Controls whether Outline items are collapsed or expanded
- `outline.icons` - Outline elements displayed with icons
- `outline.problems.badges` - Badges displayed for errors and warnings
- - `outline.problems.colors` - Colors used for errors and warnings
- `outline.problems.enabled` - Show errors and warnings on outline elements
- `outline.showArrays` - When enabled, Outline shows array-symbols.
- `outline.showBooleans` - When enabled, Outline shows boolean-symbols.
- `outline.showClasses` - When enabled, Outline shows class-symbols.
- `outline.showConstants` - When enabled, Outline shows constant-symbols.
- `outline.showConstructors` - When enabled, Outline shows constructor-symbols.
- `outline.showEnumMembers` - When enabled, Outline shows enumMember-symbols.
- `outline.showEnums` - When enabled, Outline shows enum-symbols.

## Related information

[AL development environment](devenv-reference-overview.md)  
[AL formatter](devenv-al-formatter.md)  
