---
title: "Compiler Error AL0570"
description: "The symbol '{0}' results in the same translation ID as one or more other symbols."
ms.author: solsen
ms.date: 05/14/2024
ms.topic: reference
author: SusanneWindfeldPedersen
ms.reviewer: solsen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Compiler Error AL0570

[!INCLUDE[banner_preview](../includes/banner_preview.md)]

The symbol '{0}' results in the same translation ID as one or more other symbols. Rename symbol to resolve the problem.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

This diagnostic typically happens when you have multiple labels or variables with the same name within the same codeunit or scope. To resolve this error, you need to rename the conflicting symbols to ensure each has a unique translation ID.

## Related information  
[Get Started with AL](../devenv-get-started.md)  
[Developing Extensions](../devenv-dev-overview.md)  