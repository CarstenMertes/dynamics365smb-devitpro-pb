---
title: "AppSourceCop Error AS0059"
description: "Application database tables and reserved application tables should be used only as temporary tables in a multi-tenant environment."
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
# AppSourceCop Error AS0059
Reserved database tables are read-only in a multi-tenant environment

## Description
Application database tables and reserved application tables should be used only as temporary tables in a multi-tenant environment. Writing to these tables can lead to runtime errors or unexpected behavior.

[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also  
[AppSourceCop Analyzer](appsourcecop.md)  
[Get Started with AL](../devenv-get-started.md)  
[Developing Extensions](../devenv-dev-overview.md)  