---
title: "OnUpgradePerCompany Trigger"
description: "OnUpgradePerCompany trigger in AL for Business Central."
ms.date: 04/01/2021
ms.topic: reference
author: blrobl
---

# OnUpgradePerCompany Trigger
Runs during the upgrade of an extension.

## Applies to  
-  Upgrade codeunits. These codeunits have the [SubType Property \(Codeunit\)](../properties/devenv-subtype-codeunit-property.md) set to **Upgrade**.  

> [!NOTE]  
>  This trigger is also available in upgrade codeunits for the base application, not just for extensions.  

## Remarks  
It is used to perform the actual upgrade. If an error occurs during runtime the extension upgrade is canceled.

This trigger is run once for each company in the database, and it is executed within its own system session for the company.

## See Also  
 [Triggers](devenv-triggers.md)  
 [Codeunit Triggers](devenv-codeunit-triggers.md)