---
title: "DataScope system option"
description: "Identifies the scope of stored data in the isolated storage."
ms.author: solsen
ms.date: 08/08/2025
ms.topic: reference
author: SusanneWindfeldPedersen
ms.reviewer: solsen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# DataScope option type
> **Version**: _Available or changed with runtime version 2.0._

Identifies the scope of stored data in the isolated storage.

## Members
|  Member  |  Description  |
|----------------|---------------|
|Module|Indicates that the record is available in the scope of the app(extension) context.|
|Company|Indicates that the record is available in the scope of the company within the app context.|
|User|Indicates that the record is available for a user within the app context.|
|CompanyAndUser|Indicates that the record is available for a user and specific company within the app context.|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)


## Related information

[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  
[Isolated Storage](../../devenv-isolated-storage.md)