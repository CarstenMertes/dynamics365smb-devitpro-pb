---
title: "Format Property"
description: "Sets the formats of the source expression for various data types."
ms.author: solsen
ms.custom: na
ms.date: 12/08/2022
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Format Property
> **Version**: _Available or changed with runtime version 1.0._

Sets the formats of the source expression for various data types.

## Applies to
-   Xml Port

## Property Value

|Value|Available or changed with|Description|
|-----------|-----------|---------------------------------------|
|**Xml**|runtime version 1.0|Allows to work with XML documents. This is the default value.|
|**VariableText**|runtime version 1.0|Allows to work with variable text files.|
|**FixedText**|runtime version 1.0|Allows to to work with fixed-width text fields.|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Syntax

```AL
Format = VariableText;
```
  
## Remarks  

This property supports CSV (comma separated values) export files and XML files. The available options are:  
  
- XML  
- VariableText  
- FixedText  

The default value for the **Format** property is **XML**, which allows to work with XML documents. 

If you want to work with variable text files, the **Format** property must be set to **VariableText** and if you want to work with fixed-width text fields, it must be set to **FixedText**.

You can configure the text file's default settings by using the properties [TextEncoding (XMLports) Property](devenv-textencoding-property.md), 
[TableSeparator Property](devenv-tableseparator-property.md),
[RecordSeparator Property](devenv-recordseparator-property.md),
[FieldSeparator Property](devenv-fieldseparator-property.md) and
[FieldDelimiter Property](devenv-fielddelimiter-property.md).

## See Also  

[Properties](devenv-properties.md)
