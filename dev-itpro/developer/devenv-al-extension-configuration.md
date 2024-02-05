---
title: AL Language extension configuration
description: Description of the AL Language extension settings in Visual Studio Code for Business Central.
author: SusanneWindfeldPedersen
ms.custom: na
ms.date: 08/30/2023
ms.reviewer: na
ms.topic: conceptual
ms.author: solsen
ms.collection: get-started
---

# AL Language extension configuration

[!INCLUDE[2019_releasewave2.md](../includes/2019_releasewave2.md)]

[!INCLUDE [getstarted-contributions](includes/getstarted-contributions.md)]

The AL Language extension has many settings that can be defined for a specific user or for a workspace. To activate the settings, press <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>, and then choose **Preferences: Open Settings (UI)** for workspace settings, or choose **Preferences: Open User Settings** for user settings. Under **Extensions**, and **AL Language extension configuration**, you'll find the settings that are available for the AL Language extension. If a setting is not available through the UI, you can edit it directly in the `settings.json` file. For tips on how to optimize Visual Studio Code, see [Optimizing Visual Studio Code for AL Development](devenv-optimize-visual-studio-code.md).

## Settings

The following table describes the user and workspace settings for the AL Language extension:

|Setting|Value|
|-------|-----|
|Are Profile Lenses Supported|Specifies whether statement lenses are supported for the profiler.|
|Assembly Probing Paths|Sets the list of directory paths where the compiler searches for referenced .NET assemblies. For example: `"al.assemblyProbingPaths": ["./.netpackages", "C:/Program Files/Assemblies"]`|
|Are Profile Lenses Supported| Enables the Profiler CodeLens for AL, default value is `true`. Syntax is `"al.areProfileLensesSupported": true`. For more information, see [AL Profiler Overview](devenv-al-profiler-overview.md).|
|Browser|Specifies the browser in which to open the [!INCLUDE[prod_short](includes/prod_short.md)] client when launching the application from Visual Studio Code.|
|Background Code Analysis|Specifies whether the code analysis should be performed in the background. From runtime 11.0, this setting has three different options; <br>`File` (default), which performs analysis in the background<br>`Project`, which forces analysis to be performed on the entire project, with a significant performance penalty - advised only for high-performance machines<br>`None`, which switches off background analysis entirely, so that it'll only run during a full build<br>For more information, see [Code analysis performance configuration](devenv-code-analysis-performance-configuration.md).|
|Code Analyzers|Sets the list of paths to code analyzers to use for performing code analysis. For example: `"al.codeAnalyzers": ["${AppSourceCop}", "${CodeCop}"]`.|
|Compilation Options|Specifies the compilation options;  <br>`continueBuildOnError` - specifies if build should continue even if errors are found. The default and recommended value from a performance point of view is `false`. Set the value to `true` to continue building the project, even if errors are found.  It requires `al.incrementalBuild` to be `false`. <br>`delayAfterLastDocumentChange` - specifies the number of milliseconds to wait after the last buffer changes before getting document diagnostics. After changing the value of this option, you must restart Visual Studio Code for it to take effect. Default value is `800`. <br> `delayAfterLastProjectChange` - specifies the number of milliseconds to wait after the last buffer changes before getting complete diagnostics. After changing the value of this option, you must restart Visual Studio Code for it to take effect. Default value is `4000`.  <br> `maxDegreeOfParallelism` - specifies the maximum number of concurrent tasks the compiler should use when compiling the project. Default value is `2`. <br> `parallel` - controls whether to use concurrent builds. Default value is `true`.  <br>`generateReportLayout`- controls whether the compiler will generate Report Layout files when building the package. Default value is `true`. <br> `outFolder` - Specifies the folder where the compiler should place the resulting .app file. If not specified, the compiler will place the resulting .app file in the project folder.|
|Editor Services Log Level|Sets the logging verbosity level for the AL Language Editor Services host executable. Possible values are `Verbose`, `Normal`, `Warning`, and `Error`.|
|Editor Services Path|Specifies the path to the Editor Services host executable.|
|Enable Code Actions|Specifies whether code actions should be enabled for all source files in the current project. Default is `false`.|
|Enable Code Analysis|Specifies whether code analysis should be performed for all source files in the current project. Default is `false`. If this is set to `true`, you must specify the **Code Analyzers** setting with the list of code analyzers to use.|
|Enable Script IntelliSense|Specifies whether IntelliSense should be enabled for control add-in script files. Turn this off, if it interferes with advanced JavaScript or TypeScript configurations. Default is `true`.|
|Incognito|Specifies whether to open the browser in Incognito/InPrivate mode when launching the application from Visual Studio Code. This option will take effect only if the **Browser** option is set to a non-default value.|
|Incremental Build| Specifies whether a project, when it's built using <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>B</kbd>, or <kbd>Ctrl</kbd>+<kbd>F5</kbd>, or <kbd>F5</kbd>, will reuse the last known tracked compilation, which will enhance the compilation time significantly. For more information about project to project references, see [Working with multiple projects and project references](devenv-work-workspace-projects-references.md). <br> **Note:** Setting this to `true` won't do an end-to-end build, as it's depending on an already-compiled state. To get a clean, full build, this flag must be set to `false`. Default is `false`. <br> **Important:** If this setting is enabled, then all translations will be ignored, even though the `"features": [ "TranslationFile" ]` setting is specified in the `app.json` file. For more information, see [Working with Translation Files](devenv-work-with-translation-files.md).|
|Package Cache Path|Sets the directory path where reference symbol packages are located. **With [!INCLUDE [prod_short](includes/prod_short.md)] 2023 release wave 1**, you can specify multiple file locations for symbol packages. If you specify multiple paths, the first entry is used as the directory to store the downloaded symbols. Syntax is `"al.packageCachePath": ["./.alpackages", "./.alternativePackages"]`.|
|Profiler Colors|Specifies the colors used to define the application types in the profiler output. Accepts valid color names, hex codes, and rgba() values. The properties are `systemApplication` - default color `green`, `baseApplication` - default color `magenta`, and `extension` - default color `yellow`.|
|Rule Set Path|Sets the path to the file containing the customized rules to use when running code analysis. For more information, see [Ruleset for the Code Analysis Tool](devenv-rule-set-syntax-for-code-analysis-tools.md).|
|Snapshot Debugger Lines Hit Decoration | Specifies the decoration values for a line that is hit by the snapshot debugger. Syntax is `al.snapshotDebuggerLinesHitDecoration`.|
|Show Explorer at Startup|Specifies whether the AL Explorer is shown at startup. Options are: `Always`, `Never`, and `Once`. Default is `Once`. Syntax is `al.showExplorerAtStartup`.|
|Show Home at Startup|Specifies whether the AL Developer Home is shown at startup. Options are: `Always`, `Never`, and `WhenUpdated`. Default is `WhenUpdated`. Syntax is `al.showHomeAtStartup`.|
|Snapshot Debugging Path|Sets the directory path where the snapshot debugger sources are located. Default is `./.snapshot`.|
|Snapshot Output Path|Sets the directory path where snapshot files are saved. Default is `./.snapshots`.|
|Statement Lens Minimum|Sets the lower limit for the time spent on statement execution expressed in milliseconds. Default value is `500`. Syntax is `"al.statementLensMin": 100`. For more information, see [AL Profiler Overview](devenv-al-profiler-overview.md).|
|Use Legacy Runtime|Use the .NET Framework runtime for hosting the language service instead of the .NET Core runtime. Enabling this might result in a reduced level of performance. <br>**Note:** From extension version 11.0 this setting has been deprecated and has no effect.|
|Generate PermissionSet for Extension Objects | Generate a permission set as an AL object. Syntax is `al.generatePermissionSetForExtensionObjects`. When invoking the command, the developer can choose to create a new permission file or select an existing file to update.|
|Inlayhints > Function Return Types| Switch on/off inlay hints for implicit return types on method signatures.|
|Inlayhints > Parameter Names| Switch on/off inlay hints for parameter names.|
|AL-Go Suggested Folder| Sets the suggested folder when using AL:Go! command. Can be set per user or per workspace.|

## See Also

[AL Development Environment](devenv-reference-overview.md)  
[Debugging in AL](devenv-debugging.md)  
[JSON Files](devenv-json-files.md)  
[Working with multiple projects and project references](devenv-work-workspace-projects-references.md)  
