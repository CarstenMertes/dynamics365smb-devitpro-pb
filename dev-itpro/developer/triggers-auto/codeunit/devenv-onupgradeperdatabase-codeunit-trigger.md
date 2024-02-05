---
title: "OnUpgradePerDatabase (Codeunit) Trigger"
description: "Runs during the upgrade of an extension."
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

# OnUpgradePerDatabase (Codeunit) Trigger
> **Version**: _Available or changed with runtime version 1.0._

Runs during the upgrade of an extension.

> [!IMPORTANT]
> The [Subtype Property](../../properties/devenv-subtype-property.md) must be set to **Upgrade** in the Codeunit.

## Syntax
```AL
trigger OnUpgradePerDatabase()
begin
    ...
end;
```



[//]: # (IMPORTANT: END>DO_NOT_EDIT)

> [!NOTE]  
>  This trigger is also available in upgrade codeunits for the base application, not just for extensions.  

## Remarks  
It is used to perform the actual upgrade. If an error occurs during runtime the extension upgrade is canceled.

This trigger is run once in the entire upgrade process, in a single system session that does not open any company.

## See Also  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  
