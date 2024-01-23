---
title: "PerTenantExtensionCop Error PTE0006"
description: "Encryption key functions must not be invoked."
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
# PerTenantExtensionCop Error PTE0006
Encryption key functions must not be invoked.

## Description
Encryption key functions must not be invoked.

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

This rule validates that your extension does not invoke the following methods because they are only supported on-premises:

- [CreateEncryptionKey](../methods-auto/system/system-createencryptionkey-method.md)
- [DeleteEncryptionKey](../methods-auto/system/system-deleteencryptionkey-method.md)
- [ExportEncryptionKey](../methods-auto/system/system-exportencryptionkey-method.md)
- [ImportEncryptionKey](../methods-auto/system/system-importencryptionkey-method.md)

> [!Note]
> [!INCLUDE[on_prem_only](../includes/on_prem_only.md)]

## How to fix this diagnostic?

You must remove the references to the encryption key methods from your AL code.

## See Also  
[PerTenantExtensionCop Analyzer](pertenantextensioncop.md)  
[Get Started with AL](../devenv-get-started.md)  
[Developing Extensions](../devenv-dev-overview.md)  