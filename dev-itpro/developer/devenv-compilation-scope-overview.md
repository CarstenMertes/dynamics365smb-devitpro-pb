---
title: Compilation scope overview
description: This article explains the configuration and compilation scope for publishing the extension.
ms.date: 05/18/2025
ms.topic: overview
author: SusanneWindfeldPedersen
ms.reviewer: solsen
---

# Compilation scope overview

In [!INCLUDE [prod_short](includes/prod_short.md)], there are different layers to manage what can be published to the server and accessed from within a project.

## Configure extension target on the server

By setting the **Allowed Extension Target Level** flag in the server configuration, you control what can be published to the server by setting the **Cloud** or **OnPrem** flag. Learn more in [Configuring Business Central server](../administration/configure-server-instance.md#Development). 

## Configure extension target for an extension

In the manifest of an extension (the app.json file), you can set the **target** property to specify the compilation target of an extension. The available values are `Internal`, `Extension`, `OnPrem`, and `Cloud`. 

> [!IMPORTANT]  
> The `Internal` and  `Extension` values have been deprecated, starting with runtime 4.0 and replaced by the `OnPrem` and `Cloud` respectively. 

The `target` property informs the compiler, which APIs can be used within the current project. 

- If you specify `"target":"OnPrem"`, you can use any platform APIs and .NET types. This is the most *permissive* target. It's only if you specify this target, that you can use methods marked with `Scope('OnPrem')` or tables with the property [Scope (tables)](properties/devenv-scope-table-property.md) set to `OnPrem`. 
- If you specify `"target":"Cloud"`, you can only use APIs that are safe for use in a cloud environment. If the target is set to `Cloud`, the extension can't use any method marked with `Scope('OnPrem')` or table with the property `Scope` set to the `OnPrem`. For example, if you have two extensions; A and B. Extension A has an `app.json` target setting `"target": "OnPrem"` and defines a method with the [Scope attribute](attributes/devenv-scope-attribute.md) set to `[Scope('OnPrem')]`. Extension B has a dependency on extension A and extension B has an app.json target setting `"target": "Cloud"` and tries to call the method in extension A marked with scope `OnPrem`, you get a compile error when you're trying to compile extension B. Learn more in [JSON files](devenv-json-files.md).

 > [!NOTE]  
 > A table with the property `Scope` set to `OnPrem` carries this scope forward to every other object that might refer it as `SourceTable`, even if those elements are declared within the same extension. <br> 

## Methods and tables scope

Methods can be marked with the `[Scope()]` attribute to specify the compilation target and tables can be marked with the `Scope` property. Both instruct the compiler, which targets the method or table can be used in. Learn more in [Scope attribute](attributes/devenv-scope-attribute.md) and [Scope (table) property](properties/devenv-scope-table-property.md).

## Related information

[AL development environment](devenv-reference-overview.md)  
[Developing extensions in AL](devenv-dev-overview.md)  
[JSON files](devenv-json-files.md)  
[Scope attribute](/dynamics365/business-central/dev-itpro/developer/attributes/devenv-scope-attribute)  
[Scope (table) property](properties/devenv-scope-table-property.md)  
[Configuring Business Central server](../administration/configure-server-instance.md)