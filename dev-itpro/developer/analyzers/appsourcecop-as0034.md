---
title: "AppSourceCop Error AS0034"
description: "Modifying table properties can lead to destructive changes that will break the upgrade of existing installations and dependent extensions."
ms.author: solsen
ms.date: 08/08/2025
ms.topic: reference
author: SusanneWindfeldPedersen
ms.reviewer: solsen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# AppSourceCop Error AS0034
Unsupported table property change

## Description
Modifying table properties can lead to destructive changes that will break the upgrade of existing installations and dependent extensions.

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

This error occurs when a table property is modified in a way that is not supported. Modifying table properties can lead to destructive changes, which can break the upgrade process for existing installations and dependent extensions.

## How to fix this diagnostic?

To resolve this error, you need to avoid making unsupported changes to table properties. Here are the steps:

1. Locate the table property in your code that is causing the error.
2. Change the property back to its original value or to a supported value.

## Related information  

[AppSourceCop Analyzer](appsourcecop.md)  
[Get Started with AL](../devenv-get-started.md)  
[Developing Extensions](../devenv-dev-overview.md)  