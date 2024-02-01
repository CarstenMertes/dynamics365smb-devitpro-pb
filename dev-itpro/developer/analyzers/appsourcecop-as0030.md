---
title: "AppSourceCop Error AS0030"
description: "Pages that have been published must not be renamed because it will break dependent extensions."
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
# AppSourceCop Error AS0030
Pages that have been published must not be renamed.

## Description
Pages that have been published must not be renamed because it will break dependent extensions.

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

It is not allowed to rename pages which have been published. This will break dependent extensions which:
- are referencing this page from code by name,
- are extending the page by name using a page extension,
- are customizing the page by name using page customizations.

It is allowed to rename page extensions, because page extensions cannot be referenced by name from a dependent extension.

## How to fix this diagnostic?

Revert the change made on the page in order to keep the name defined previously. 

If the rename was done in order to define the UI display of the page, consider using the [Caption](../properties/devenv-caption-property.md) property instead.

If the rename was done in order to comply with naming rules such as [AS0011](appsourcecop-as0011.md), consider obsoleting the page and introducing a new one.

## Examples of errors for dependent extensions

Renaming a page has the same consequences as removing it for dependent extensions which are referencing it by name. You can then find examples of errors reported in dependent extensions in rule [AS0029](appsourcecop-as0029.md).

## See Also  
[AppSourceCop Analyzer](appsourcecop.md)  
[Get Started with AL](../devenv-get-started.md)  
[Developing Extensions](../devenv-dev-overview.md)  
