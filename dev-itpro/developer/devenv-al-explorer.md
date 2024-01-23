---
title: AL Explorer
description: The AL Explorer for Business Central lets you explore and navigate objects in extensions.  
author: SusanneWindfeldPedersen
ms.author: solsen
ms.reviewer: solsen

ms.topic: conceptual
ms.date: 09/21/2023
ms.custom: bap-template
ms.collection: get-started
---

# AL Explorer

[!INCLUDE [2023_releasewave1](../includes/2023_releasewave1.md)]

[!INCLUDE [getstarted-contributions](includes/getstarted-contributions.md)]

The **AL Explorer** provides a tool that allows you to explore, navigate, and better understand objects in extensions. You can drill down into object details, dependencies, and extension points, without looking at the code. With the **AL Explorer**, you have an overview of high-level structures of extensions that can help you specify new features, or do light troubleshooting.

The **AL Explorer** has four tabs: **OBJECTS**, **EVENTS**, **APIS**, and **EXTENSIBLE ENUMS**. For each of these categories, you can apply filtering for type, module, related table, or namespace, you can set bookmarks, and go to source code. For tables, pages, and report objects, you can choose to run these objects directly from the explorer window, on either a local machine or a tenant. You can get an overview of all objects in a given app scope, for example, a workspace or a selected project, and you can search in object names, and group objects by type.

:::image type="content" source="media/al-explorer.png" alt-text="The AL Explorer window with tabs and buttons to drill-down into code":::

## Settings

You can choose when to show the **AL Explorer** as you start up Visual Studio Code, the default is that **AL Explorer** is shown once at startup. To change the default, go to user or workspace settings, press <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>, and then choose **Preferences: Open Settings (UI)** for workspace settings, or choose **Preferences: Open User Settings** for user settings. Under **Extensions**, and **AL Language extension configuration**, change the **Show Explorer at startup** to a different value. For more information, see [AL Language extension configuration](devenv-al-extension-configuration.md).

## Go to source code

For a selected object, use the **Source** button to go to source code to develop, read, or understand it, or use it to add breakpoints as part of troubleshooting.

> [!NOTE]  
> When you choose **Source** on a given object, the resource exposure policy, which applies to the object, may prevent the entire source code to be shown. In this case, you'll see only fragments of the code. 

## Bookmarks

In the rightmost column, you can bookmark objects used frequently to filter a list of objects to view only the bookmarked ones, for example, when navigating between the objects that you currently work on. Choose the `*` to bookmark an object. Use the **Module** dropdown to filter only on **Bookmarked objects**.

## View extension points

The **EVENTS**, **APIS**, and **EXTENSIBLE ENUMS** tabs provide an overview of available extension points and extensible enums that implement interfaces. On any given event, you can choose the **Subscribe** button, which copies a code snippet with the event subscriber syntax into the clipboard, and you can paste that into a codeunit to get started.

## See also

[AL Home](devenv-al-home.md)  
[Developing Extensions in AL](devenv-dev-overview.md)