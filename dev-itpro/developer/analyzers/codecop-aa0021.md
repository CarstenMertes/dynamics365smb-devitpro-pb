---
title: "CodeCop Warning AA0021"
description: "Variable declarations should be ordered by type."
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
# CodeCop Warning AA0021
Variable declarations should be ordered by type.

## Description
Variable declarations should be ordered by type. In general, object and complex variable types are listed first followed by simple variables.

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

Object and complex variable types must be listed first, and then simple variables. The order is: Record, Report, Codeunit, XmlPort, Page, Query, Notification, BigText, DateFormula, RecordId, RecordRef, FieldRef, and FilterPageBuilder. The rest of the variables are not sorted.

## See Also  
[CodeCop Analyzer](codecop.md)  
[Get Started with AL](../devenv-get-started.md)  
[Developing Extensions](../devenv-dev-overview.md)  