---
title: "Lookup property"
description: "Specifies if a page field has a lookup window."
ms.author: solsen
ms.date: 08/26/2024
ms.topic: reference
author: SusanneWindfeldPedersen
ms.reviewer: solsen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Lookup Property
> **Version**: _Available or changed with runtime version 1.0._

Specifies if a page field has a lookup window.

## Applies to
-   Page Field

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

  
## Property Value

**True** if you want a lookup for the field; otherwise, **false**. The default value is **false**.  

## Syntax

```AL
Lookup = true;
```
  
## Remarks

By default, a lookup provides a list of records in the table. Using this list, users can select a record and retrieve information from it into this control.  
  
## Related information

[LookupPageID Property](devenv-lookuppageid-property.md)