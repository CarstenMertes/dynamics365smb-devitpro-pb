---
title: Code analysis performance configuration
description: Guidance on troubleshooting and optimizing code analysis performance in AL for Business Central.
author:  BazookaMusic 
ms.author: sodragon
ms.reviewer: solsen

ms.topic: conceptual
ms.date: 01/09/2023
ms.custom: bap-template
---

# Code analysis performance configuration

[!INCLUDE [2023_releasewave1](../includes/2023_releasewave1.md)]

This article gives an overview of the tools and configuration options, which are offered to ensure that the code analysis tool performs adequately on different workspace sizes and machine configurations. This includes controlling the scope of the code analysis tool during live editing and troubleshooting tips to identify and suppress long-running code analysis rules.

To activate the settings described in this article, press <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>, and then choose **Preferences: Open Settings (UI)** for workspace settings, or choose **Preferences: Open User Settings** for user settings. Under **Extensions**, and **AL Language extension configuration**, you'll find the settings that are available for the AL Language extension. If a setting is not available through the UI, you can edit it directly in the `settings.json` file.

## Background code analysis - scope

When you edit a project with code analysis enabled, the default behavior is that code analysis will run in the background. This means that, every change will trigger a recalculation of the code analysis diagnostics. The analysis may run in the scope of the currently active file or the entire open project. The default scope of the analysis is determined by the extension based on the size of the workspace. For smaller projects, analysis will be performed on the entire active project and its dependent projects. When a larger workspace is detected by the extension, it will by default perform analysis only on the active file. This ensures that the analysis can run interactively regardless of the size of the project. The downside is that code analysis diagnostics won't be displayed for files, which aren't focused in the editor.

The scope of the code analysis can be overridden through the `backgroundCodeAnalysis` setting. Its default value is `File`, which corresponds to the behavior described in the previous paragraph. The `Project` value forces analysis to be performed on the entire project, with a significant performance penalty. For this reason, it's advised only for high-performance machines. The `None` option turns off background analysis entirely, so that it will only run during a full build.

It's possible to override the scope for a user or a specific workspace by using the appropriate settings file and not specifying the scope explicitly on the project settings.

## Troubleshooting long-running code analysis rules

It's possible to get statistics for the runtime of individual code analysis rules, with the intent of switching them off selectively if they're long-running on a specific project. Switching it off can be useful in the case where the default code analysis scope isn't performant enough, or when it's a requirement to run code analysis for an entire project. By enabling the setting `outputAnalyzerStatistics`, a detailed overview of the runtime of each analysis rule and its corresponding diagnostics will be printed to the output. The output will be similar to the snippet shown in this section, where the total time and percentage of time spent by each rule is displayed in the appropriate column.

```
Time (s)    %   Analyzer (Related Diagnostics)
   0.092   73   CodeCop
   0.032   24      Application Area Has Invalid Value (AA0189, AA0199, AA0200, AA0201)
   0.028   22      Rec Db Invocation Analyzer (AA0181, AA0233)
   0.028   22      Do Not Declare Variables That Are Unused (AA0137)
   0.001   <1      Variables Names Analyzer (AA0073, AA0237, AA0072)
  <0.001   <1      Use Lowercase For Language Keywords (AA0241)
  <0.001   <1      Email And Phone No Must Not Be Present In The Source (AA0240)
  ...
```

After a rule is identified as long-running, it can be switched off in the [ruleset](devenv-rule-set-syntax-for-code-analysis-tools.md) of the project. This is achieved by adding an entry for all of its related diagnostics with the action property set to `None`.

## Next steps

The next step is to access the settings and configure your projects to achieve satisfactory performance.

## See Also

[Using the Code Analysis Tools](devenv-using-code-analysis-tool.md)  
[Using the Code Analysis Tools with the ruleset](devenv-using-code-analysis-tool-with-rule-set.md)
[Ruleset for the Code Analysis Tool](devenv-rule-set-syntax-for-code-analysis-tools.md)
[AL Language Extension Configuration](devenv-al-extension-configuration.md)