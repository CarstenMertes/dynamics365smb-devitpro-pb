---
title: "AutoReplace property"
description: "Sets whether imported records automatically replace existing records with the same primary key."
ms.author: solsen
ms.date: 08/26/2024
ms.topic: reference
author: SusanneWindfeldPedersen
ms.reviewer: solsen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# AutoReplace Property
> **Version**: _Available or changed with runtime version 1.0._

Sets whether imported records automatically replace existing records with the same primary key.

## Applies to
-   Xml Port Table Element

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Property Value 
 **True** if the records are replaced; otherwise, **false**. The default value is **false**.  

## Syntax
```AL
AutoReplace = true;
```
  
## Remarks
 If a record with the same primary key is found in the database, then the record is initialized with the initial value for each field and then populated with the values in the imported record. Any field in the record that is not present in the imported record retains its initial value. For more information about initial values, see [InitValue Property](devenv-initvalue-property.md).  
  
> [!WARNING]  
>  If this property is set to **true**, then the [AutoUpdate Property](devenv-autoupdate-property.md) has no effect.  
  
## Related information  
 [AutoUpdate Property](devenv-autoupdate-property.md)   
 [AutoSave Property](devenv-autoSave-property.md)