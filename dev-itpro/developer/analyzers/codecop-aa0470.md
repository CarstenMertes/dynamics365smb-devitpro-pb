---
title: "CodeCop Warning AA0470"
description: "Provide an explanation that describes the content of each of the placeholders."
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
# CodeCop Warning AA0470
Placeholders should have a comment explaining their content.

## Description
Provide an explanation that describes the content of each of the placeholders.

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Reason for the rule

Documentation of placeholders is required in order to enable translators to properly know the construct of the label to be translated.

## Bad code example
```AL
MissingNodeErr: Label 'Cannot find an XML node that matches %1 or %2.'; 
```

## Good code example
```AL
MissingNodeErr: Label 'Cannot find an XML node that matches %1 or %2.', Comment = '%1 = XML node name ; %2 = Parent XML node name';
```

## See Also  
[CodeCop Analyzer](codecop.md)  
[Get Started with AL](../devenv-get-started.md)  
[Developing Extensions](../devenv-dev-overview.md)  