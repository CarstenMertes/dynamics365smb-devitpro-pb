---
title: "Using the code analysis tool"
description: "Using static code analysis tool on an AL project."
author: SusanneWindfeldPedersen
ms.date: 06/23/2022
ms.topic: conceptual
ms.author: solsen
---

# The code analysis tool

This article shows you how to use static code analysis tool on an AL project from within Visual Studio Code.

## Enable the code analysis

Follow these steps to create a basic project in AL. 

1. Select <kbd>Alt</kbd>+ <kbd>A</kbd>, <kbd>Alt</kbd>+<kbd>L</kbd> to create a new project.
2. Open the Command Palette **Ctrl+Shift+P** and choose either **User Settings** or **Workspace Settings**.
3. Under **Extensions**, go to **Al Language extension configuration**. When you scroll down, you'll find Code Analyzers section, choose **Edit in settings.json**.
4. Set the `al.enableCodeAnalysis` in the settings file to `true`. <br> `"al.enableCodeAnalysis": true`
5. In the `al.codeanalyzers` setting, use <kbd>Ctrl</kbd>+<kbd>Space</kbd> to pick from the available code analyzers. Separate the list of code analyzers with commas. For more information about the available analyzers, see [AppSourceCop](analyzers/appsourcecop.md), [CodeCop](analyzers/codecop.md), [PerTenantExtensionCop](analyzers/pertenantextensioncop.md), and [UICop](analyzers/uicop.md).

At this point, the selected analyzers run on your project. Next, add some code to the project that will, in the following example, be used to demonstrate a violation of the AA0001 **"There must be exactly one space character on each side of a binary operator such as := + - AND OR =."** code analysis rule. 

> [!NOTE]  
> By default, code analysis runs in the background.

## Add your own code to the project

In the Visual Studio Code Explorer, open the `HelloWorld.al` file and replace the existing code with the following code:

```AL
pageextension 50100 CustomerListExt extends "Customer List"
{
    trigger OnOpenPage();
    var
        result: Integer;
    begin        
        // The following line will trigger the warning
        // AA0001 "There must be exactly one space character on each side 
        // of a binary operator such as := + - AND OR =." 
        result := 2+2; 
        Message('2 + 2 = ' + Format(result));
    end;
}
```

## View the results of the code analysis

The code analysis tools run in the background. You'll see the faulty expression underlined and the warning **"There must be exactly one space character on each side of '+'."** display if you move cursor over the underlined code.
You can also view the list of issues by selecting the **View** tab of Visual Studio Code and choosing the **Problems** option.

Using the <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>B</kbd> shortcut to build your project runs the code analysis tools on the entire project and the detected issues display in the **Output** window of Visual Studio Code. For more information about AL keyboard shortcuts, see [Keyboard shortcuts](devenv-keyboard-shortcuts.md).

## Code analyzers

A code analyzer is a library that builds on the compiler's functionality to offer enhanced analysis of the syntax and semantics of your code at build time.
The [!INCLUDE[d365al_ext_md](../includes/d365al_ext_md.md)] for Visual Studio Code contains four analyzers:

- **CodeCop** is an analyzer that enforces the official AL Coding Guidelines. For more information about the CodeCop rules, see [CodeCop Analyzer Rules](analyzers/codecop.md).
- **PerTenantExtensionCop** is an analyzer that enforces rules that must be respected by extensions meant to be installed for individual tenants. For more information about the PerTenantExtensionCop rules, see [PerTenantExtensionCop Analyzer Rules](analyzers/pertenantextensioncop.md).
- **AppSourceCop** is an analyzer that enforces rules that must be respected by extensions meant to be published to Microsoft AppSource. For more information about the AppSourceCop rules, see [AppSourceCop Analyzer Rules](analyzers/appsourcecop.md).
- **UICop** is an analyzer that enforces rules that must be respected by extensions that are meant to customize the web client. For more information about the UserInterfaceCop rules, see [UICop Analyzer Rules](analyzers/uicop.md).

## <a  name="largeprojects"></a>Enable code analysis on large projects

To improve performance while running code analysis on large projects, you can follow the performance tips in [Code Analysis Performance Configuration](devenv-code-analysis-performance-configuration.md).
  
## See Also

[Using the Code Analysis Tools with the Ruleset](devenv-using-code-analysis-tool-with-rule-set.md)  
[Ruleset for the Code Analysis Tool](devenv-rule-set-syntax-for-code-analysis-tools.md)  
[Development in AL](devenv-dev-overview.md)  
[Directives in AL](directives/devenv-directives-in-al.md)  
[Debugging in AL](devenv-debugging.md)  
[AL Language Extension Configuration](devenv-al-extension-configuration.md)  

