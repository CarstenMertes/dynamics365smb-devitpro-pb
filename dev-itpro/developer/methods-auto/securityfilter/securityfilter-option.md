---
title: "SecurityFilter system option"
description: "Specifies how security filters are applied to the record."
ms.author: solsen
ms.date: 08/26/2024
ms.topic: reference
author: SusanneWindfeldPedersen
ms.reviewer: solsen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# SecurityFilter Option Type
> **Version**: _Available or changed with runtime version 1.0._

Specifies how security filters are applied to the record.

## Members
|  Member  |  Description  |
|----------------|---------------|
|Validated|All security filters are applied to this instance of the record and if any code tries to access a record that is outside the range of the security filters, then an error occurs.|
|Filtered|All security filters are applied to this instance of the record.|
|Ignored|All security filters are ignored for this instance of the record.|
|Disallowed|Security filters are not allowed on the record. If any security filters are set, then you receive an error when you run the object that uses this instance of the record.|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## Related information  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  