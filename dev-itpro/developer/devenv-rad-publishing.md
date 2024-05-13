---
title: "Work with Rapid Application Development"
description: "Describes what Rapid Application Development is and how you publish using RAD."
author: SusanneWindfeldPedersen
ms.date: 08/08/2022
ms.topic: conceptual
ms.author: solsen
---

# Work with Rapid Application Development

When working with Visual Studio Code and [!INCLUDE[d365fin_long_md](includes/d365fin_long_md.md)], you can benefit from Rapid Application Development (RAD) on large code projects. RAD allows faster development on projects with a large number of files by doing a delta compilation and publishing only on those application objects that have changed during development in Visual Studio Code. RAD publishing is an interim state and doesn't replace a full publish. 

## How RAD works

The files that have been changed by the application developer within Visual Studio Code are persisted in a special RAD (.rad) file during builds. This file is saved in the .vscode folder of the code project. RAD changes are the changes of application objects within a RAD session. Only application objects, page customization objects, and profile objects are handled for RAD. RAD changes won't be persisted during save, only during build, publish, and debug.

> [!IMPORTANT]  
> The `rad.json` file should not be modified.

> [!IMPORTANT]  
> If you change many files and close Visual Studio Code without a build (<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>B</kbd>), publish (<kbd>Ctrl</kbd>+<kbd>F5</kbd>, <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>F5</kbd>) or debug (<kbd>F5</kbd>, <kbd>Shift</kbd>+<kbd>F5</kbd>), all the RAD changes will be lost. This means that if you, in the next Visual Studio Code session perform a RAD publishing, it'll be done on the latest changes and not on the prior changes. This can lead to an incomplete published package if it succeeds. It's therefore a best practice to do a regular publish. You can always check the RAD file in the code project to see what application objects are going to be changed during publishing.

In scenarios when application IDs are renamed, or refactored it's also a best practice to first do a full publishing, and then a RAD publishing for the consecutive changes. RAD doesn't check for application ID changes and ID changes can occur in a wrongly published application.

A RAD published file won't contain the following files that are normally packaged during regular publishing: 

- Translation files
- Permission files
- Custom word and report rdl layout files  
- Table data
- Web service definitions  

These files will need to be regenerated with full publishing (<kbd>Ctrl</kbd>+<kbd>F5</kbd> ). A RAD file will be deleted as a result of a successful publishing.

> [!NOTE]  
> If RAD publishing fails, then you must do a full publishing before performing another RAD publishing. The final state of an application must be built using full publishing, and never with RAD publishing.

> [!NOTE]  
> When building using RAD, all translations will be ignored, even though the `"features": [ "TranslationFile" ]` setting is specified in the `app.json` file. For more information, see [Working with Translation Files](devenv-work-with-translation-files.md).

## RAD shortcuts

There are two commands for starting a RAD-based action. 

|Shortcut     |Description|
|-------------|-----------|
|<kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>F5</kbd>  |Start RAD publishing without debugging.|
|<kbd>Alt</kbd>+<kbd>F5</kbd>       |Start RAD with debugging.|

## See also
[Developing Extensions in AL](devenv-dev-overview.md)  
[Debugging](devenv-debugging.md)  

