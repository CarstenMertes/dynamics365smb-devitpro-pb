---
title: "AppSourceCop Error AS0091"
description: "One or more dependencies of the previous version of the extension, used as a baseline for detecting breaking changes, could not be found in the package cache folder."
ms.author: solsen
ms.custom: na
ms.date: 12/07/2021
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# AppSourceCop Error AS0091
One or more dependencies of the previous version of the extension could not be found.

## Description
One or more dependencies of the previous version of the extension, used as a baseline for detecting breaking changes, could not be found in the package cache folder.

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

This rule validates that the dependencies for the version of the extension specified as a baseline for detecting breaking changes can be found in the baseline package cache folder.

> [!NOTE]  
> The rule [AS0003](appsourcecop-as0003.md) verifies that the baseline can be found in the baseline package cache folder.

### Setting up AppSourceCop to detect breaking changes

For more information on how to set up the AppSourceCop to detect breaking changes, see [AS0003](appsourcecop-as0003.md).

## How to fix this diagnostic?

If you do not want to detect breaking changes in your extension, remove the property `version` in the AppSourceCop.json file.

If you want to detect breaking changes, verify that the version specified in the AppSourceCop.json file is correct and that the baseline's dependencies can be found in the baseline package cache.

## See Also  
[AppSourceCop Analyzer](appsourcecop.md)  
[Get Started with AL](../devenv-get-started.md)  
[Developing Extensions](../devenv-dev-overview.md)  
