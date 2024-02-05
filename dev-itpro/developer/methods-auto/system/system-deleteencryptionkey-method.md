---
title: "System.DeleteEncryptionKey() Method"
description: "Deletes an encryption key for the current tenant."
ms.author: solsen
ms.custom: na
ms.date: 07/07/2021
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# System.DeleteEncryptionKey() Method
> **Version**: _Available or changed with runtime version 1.0._

Deletes an encryption key for the current tenant.


## Syntax
```AL
 System.DeleteEncryptionKey()
```
> [!NOTE]
> This method can be invoked without specifying the data type name.



[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Example

This code example checks if encryption is configured for the tenant using the [EncryptionEnabled](../../methods-auto/system/system-encryptionenabled-method.md) method and if so, it performs the deletion of the encryption key.  

```al
if not EncryptionEnabled then  
  Error('Encryption has not been enabled.');  
  DeleteEncryptionKey();  
```

## See Also

[System Data Type](system-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)