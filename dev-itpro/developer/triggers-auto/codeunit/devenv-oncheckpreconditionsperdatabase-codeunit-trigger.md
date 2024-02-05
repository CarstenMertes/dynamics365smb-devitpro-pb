---
title: "OnCheckPreconditionsPerDatabase (Codeunit) Trigger"
description: "Runs before an extension upgrade."
ms.author: solsen
ms.custom: na
ms.date: 12/06/2022
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)

# OnCheckPreconditionsPerDatabase (Codeunit) Trigger
> **Version**: _Available or changed with runtime version 1.0._

Runs before an extension upgrade.

> [!IMPORTANT]
> The [Subtype Property](../../properties/devenv-subtype-property.md) must be set to **Upgrade** in the Codeunit.

## Syntax
```AL
trigger OnCheckPreconditionsPerDatabase()
begin
    ...
end;
```



[//]: # (IMPORTANT: END>DO_NOT_EDIT)

> [!NOTE]  
> This trigger is also available in upgrade codeunits for extensions, not just for the base application. 

## Remarks

It is used to check that certain requirements are met in order to run the upgrade.If an error occurs during runtime the extension upgrade is canceled.

This trigger is run once in the entire upgrade process, in a single system session that does not open any company.

## See Also  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  
