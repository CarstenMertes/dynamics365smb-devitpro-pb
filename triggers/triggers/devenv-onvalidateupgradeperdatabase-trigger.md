---
title: "OnValidateUpgradePerDatabase Trigger"
description: "OnValidateUpgradePerDatabase trigger in AL for Business Central."
ms.date: 04/01/2021
ms.topic: reference
author: blrobl
---

# OnValidateUpgradePerDatabase Trigger
Runs after an extension upgrade.

## Applies to  
-  Upgrade codeunits. These codeunits have the [SubType Property \(Codeunit\)](../properties/devenv-subtype-codeunit-property.md) set to **Upgrade**.  

> [!NOTE]  
>  This trigger is also available in upgrade codeunits for the base application, not just for extensions.  

## Remarks  
It is used to check that the upgrade was successful. If an error occurs during runtime the extension upgrade is canceled.

This trigger is run once in the entire upgrade process, in a single system session that does not open any company.

## See Also  
 [Triggers](devenv-triggers.md)  
 [Codeunit Triggers](devenv-codeunit-triggers.md)