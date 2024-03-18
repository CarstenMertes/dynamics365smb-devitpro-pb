---
title: "PageBackgroundTaskErrorLevel System Option"
description: "Specifies how an error in the page background task appears in the client."
ms.author: solsen
ms.custom: na
ms.date: 05/11/2021
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# PageBackgroundTaskErrorLevel Option Type
> **Version**: _Available or changed with runtime version 4.0._

Specifies how an error in the page background task appears in the client.

## Members
|  Member  |  Description  |
|----------------|---------------|
|Error|Error occuring in a page background task is displayed as an normal error in the client. This is the default value.|
|Warning|Error occuring in a page background task is displayed as an warning in the client. **Note:** Any error thrown in completion trigger will ignore this value and will be displayed in the client as a normal error.|
|Ignore|Error occuring in a page background task is not displayed in the client. **Note:** Any error thrown in completion trigger will ignore this value and will be displayed in the client as a normal error.|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  
