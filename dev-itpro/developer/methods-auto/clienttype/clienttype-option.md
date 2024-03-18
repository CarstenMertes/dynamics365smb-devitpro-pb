---
title: "ClientType System Option"
description: "Represents the type of the client executing the operation."
ms.author: solsen
ms.custom: na
ms.date: 12/15/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# ClientType Option Type
> **Version**: _Available or changed with runtime version 1.0._

Represents the type of the client executing the operation.

## Members
|  Member  |  Description  |
|----------------|---------------|
|Background|A background session.|
|ChildSession|A child session.|
|Desktop|A desktop client.|
|Management|A management client.|
|NAS|A NAS client.|
|OData|A NAS client.|
|Phone|Microsoft Dynamics Business Central Phone client.|
|SOAP|A SOAP client.|
|Tablet|Microsoft Dynamics Business Central Tablet client.|
|Web|Microsoft Dynamics Business Central Web client.|
|Windows|Microsoft Dynamics Business Central Windows client.|
|Current|Microsoft Dynamics Business Central Windows client.|
|Default|The default client.|
|ODataV4|A ODataV4 client.|
|Api|An API client.|
|Teams|Microsoft Teams client.|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

Some of these client types don't allow AL code that interacts with the user, such as using the methods `Dialog.Open`, `Dialog.Update`, `Window.Open`, `Window.Update`, or `System.Error`.

If the same codeunit needs to run both in the UI and also in the background (in a scheduled task or with a job queue entry), or in a web service call (SOAP/OData/API), then use `if GuiAllowed() then` calls to encapsulate AL code that interacts with the user. For more information, see [System.GuiAllowed() Method](../system/system-guiallowed-method.md).

## See also

[System.GuiAllowed() Method](../system/system-guiallowed-method.md)   
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  