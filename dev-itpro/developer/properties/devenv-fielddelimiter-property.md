---
title: "FieldDelimiter Property"
description: "Specifies the text delimiter for a field."
ms.author: solsen
ms.custom: na
ms.date: 06/15/2022
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# FieldDelimiter Property
> **Version**: _Available or changed with runtime version 1.0._

Specifies the text delimiter for a field.

## Applies to
-   Xml Port

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Syntax

```AL
FieldDelimiter = '<None>';
```
  
## Remarks  

**FieldDelimiter** is only used if the Format property is set to **Variable Text**. Otherwise, the setting is ignored.

The default value is “”, an empty string.    
  
You can set the field delimiter in AL code so that the XMLport can import and export records with different delimiters. For example, if your XMLport must import from a file or stream where one record uses commas and another uses an empty string, you can change the field delimiter property at run time.  
  
## See Also  

[Properties](devenv-properties.md)