---
title: "ExecutionContext System Option"
description: "Represents the context in which a session is running."
ms.author: solsen
ms.custom: na
ms.date: 06/23/2021
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# ExecutionContext Option Type
> **Version**: _Available or changed with runtime version 1.0._

Represents the context in which a session is running. In certain scenarios, for example during upgrade, the system will run a session in a special context for a limited time.

## Members
|  Member  |  Description  |
|----------------|---------------|
|Normal|The normal execution context.|
|Install|An application is being installed.|
|Uninstall|An application is being uninstalled.|
|Upgrade|An application is being upgraded.|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  