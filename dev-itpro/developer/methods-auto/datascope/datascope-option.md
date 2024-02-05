---
title: "DataScope System Option"
description: "Identifies the scope of stored data in the isolated storage."
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
# DataScope Option Type
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


## See Also

[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  
[Isolated Storage](../../devenv-isolated-storage.md)