---
title: Optimize Visual Studio code editing and building performance
description: Explains how yo configure Visual Studio Code to get better performance when editing and building AL projects.
author: jswymer
ms.custom: na
ms.date: 06/22/2022
ms.reviewer: na
ms.topic: conceptual
ms.author: jswymer
---

# Optimize Visual Studio Code for AL development

Visual Studio Code is built to handle many smaller dependent projects instead of one large project. However, as the base application isn't yet split into modules or components that allow managing the code in smaller projects, we recommend the following performance optimizations.

Open your `settings.json` file in the project (or global settings if you prefer that) selecting <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>. Set:

- `"al.enableCodeAnalysis": false` to turn off code analysis completely, read more here [Using the Code Analysis Tool](../developer/devenv-using-code-analysis-tool.md).
- `"al.backgroundCodeAnalysis": false` to turn off running code analysis in the background, but code analysis will be enabled when building with <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>B</kbd>. This is an alternative if analyzers are required with `"al.enableCodeAnalysis": true`.
- `"al.enableCodeActions": false` to turn off AL Code Actions, read more here [AL Code Actions](devenv-code-actions.md).
- `"al.incrementalBuild": true` to allow the compiler to reuse the existing background compilation for creating the package.
- `"editor.codeLens": false` to turn off code lens in Visual Studio Code, see [Code Navigation](https://code.visualstudio.com/Docs/editor/editingevolved#_reference-information).
- `"[al]": {​​​​​​​​​​"editor.formatOnSave": false }​​​​​​​​` to turn off formatting when saving a file for AL. If you still want formatting, then you can adjust what to run formatting on, and you can choose **modifications** by using the **Format On Save Mode** option.

- Add the build folder to the exclusion list for [Windows Defender](https://support.microsoft.com/help/4028485/windows-10-add-an-exclusion-to-windows-security).

## See also 
[Development in AL](devenv-dev-overview.md)   
[Best Practices for AL](../compliance/apptest-bestpracticesforalcode.md)
