---
title: Keyboard Shortcuts for AL in Visual Studio Code
description: List of keyboard shortcuts for the new development environment (Visual Studio Code).
author: SusanneWindfeldPedersen
ms.custom: na
ms.date: 04/01/2021
ms.reviewer: na
ms.topic: conceptual
ms.author: solsen
ms.collection: get-started
---

# Keyboard shortcuts for AL in Visual Studio Code

The following table provides an overview of some of the shortcut key combinations that you can use when you are working in Visual Studio Code. For a complete overview, see [Key Bindings for Visual Studio Code](https://code.visualstudio.com/docs/customization/keybindings).

## General in Visual Studio Code

|Keyboard Shortcut| Action|
|-----------------|-------|
|<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>|Show All Commands|
|<kbd>Alt</kbd>+<kbd>F6</kbd>|Download source code|
|<kbd>Alt</kbd>+<kbd>A</kbd>+<kbd>L</kbd>|AL Go! Generates a HelloWorld project|
|<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>B</kbd>|Compile and Package|
|<kbd>F5</kbd>|Compile, Package, and Publish (with debugging)|  
|<kbd>Ctrl</kbd>+<kbd>F5</kbd>|Build and publish without debugging. **Note:** The keyboard shortcut has a different meaning when debugging.|
|<kbd>F6</kbd>|Publish and open Designer|
|<kbd>Ctrl</kbd>+<kbd>F2</kbd>|Update the compiler used by the service tier(s)|

## Editing in Visual Studio Code

|Keyboard Shortcut| Action|
|-----------------|-------|
|<kbd>Ctrl</kbd>+<kbd>Space</kbd>|Look up suggestions for the current object|
|<kbd>Ctrl</kbd>+<kbd>X</kbd>|Cut|
|<kbd>Ctrl</kbd>+<kbd>C</kbd>|Copy|
|<kbd>Ctrl</kbd>+<kbd>V</kbd>|Paste|
|<kbd>Ctrl</kbd>+<kbd>F2</kbd>|Select all occurrences|
|<kbd>F12</kbd>|Go to definition|
|<kbd>Alt</kbd>+<kbd>F12</kbd>|Peek definition|
|<kbd>Shift</kbd>+<kbd>F12</kbd>|Show references|
|<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>Space</kbd>|Look up parameter hints|
|<kbd>Ctrl</kbd>+<kbd>K Ctrl</kbd>+<kbd>C</kbd>|Add line comment|
|<kbd>Ctrl</kbd>+<kbd>K Ctrl</kbd>+<kbd>U</kbd>|Remove line comment|
|<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>|Show all commands|
|<kbd>F2</kbd>|Rename (use </kbd>Enter</kbd> to rename, use <kbd>Shift</kbd>+<kbd>Enter</kbd> to preview)|
|<kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>E</kbd>|Look up events and insert event subscriber in code for a selected event.|

## Errors in Visual Studio Code

|Keyboard Shortcut| Action|
|-----------------|-------|
|<kbd>F8</kbd>|Move to the next error or warning|
|<kbd>Shift</kbd>+<kbd>F8</kbd>|Move to the previous error or warning|

## Compile and publish in Visual Studio Code

|Keyboard Shortcut| Action|
|-----------------|-------|
|<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>B</kbd>|Compile and build the solution|
|<kbd>Ctrl</kbd>+<kbd>F5</kbd>|Build and deploy|
|<kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>W</kbd>| Publish full dependency tree for the active project|

## Debugging in Visual Studio Code

For topics on debugging in AL, see [Debugging](devenv-debugging.md) and [Snapshot Debugging](devenv-snapshot-debugging.md).

|Keyboard Shortcut|Action|
|-----------------|------|
|<kbd>F5</kbd>           |Start debugging session|
|<kbd>Ctrl</kbd>+<kbd>F5</kbd>|Publish without building. **Note:** The keyboard shortcut has a different meaning when not debugging.|  
|<kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>F5</kbd>  |Start RAD publishing without debugging|
|<kbd>Alt</kbd>+<kbd>F5</kbd>      |Start RAD with debugging|
|<kbd>F7</kbd>|Start a snapshot debugging session|
|<kbd>Shift</kbd>+<kbd>F7</kbd>|List all available snapshots|
|<kbd>Alt</kbd>+<kbd>F7</kbd>|Finish a snapshot debugging session|

## Profiling in Visual Studio Code

For more information about profiling, see [AL Profiler Overview](devenv-al-profiler-overview.md)

|Keyboard Shortcut|Action|
|-----------------|------|
|<kbd>Enter</kbd> | Expand and collapse a node. |
|<kbd>Left arrow</kbd> | Collapse a node. |
|<kbd>Right arrow</kbd> | Expand a node. |
|<kbd>-</kbd> (minus) | Collapse all nodes.|
|<kbd>*</kbd> (star) | Expand one level for all nodes. Consecutive keystrokes will expand to the next level.|



## See Also

[Developing Extensions](devenv-dev-overview.md)  
[Get Started with AL](devenv-get-started.md)  
[AL Development Environment](devenv-reference-overview.md)
