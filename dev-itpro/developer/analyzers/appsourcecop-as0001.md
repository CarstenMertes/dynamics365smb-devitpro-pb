---
title: "AppSourceCop Error AS0001"
description: "Tables and table extensions that have been published must not be deleted."
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
# AppSourceCop Error AS0001
Tables and table extensions that have been published must not be deleted.

## Description
Tables and table extensions that have been published must not be deleted. This might break the upgrade of existing installations and dependent extensions.

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

This rule validates tables independently of their Accessibility or ObsoleteState, because tables are always used when synchronizing the schema defined in the extension to the database.

This rule validates table extensions independently of the ObsoleteState of their target tables. Table extensions extending a table, which is marked with obsolete state Removed must be preserved, since they're still contributing to the database schema defined by the extension.

## How to fix this diagnostic?

Revert the changes done by adding back the tables and table extensions that have been removed.

## See Also

[AppSourceCop Analyzer](appsourcecop.md)  
[Get Started with AL](../devenv-get-started.md)  
[Developing Extensions](../devenv-dev-overview.md)
