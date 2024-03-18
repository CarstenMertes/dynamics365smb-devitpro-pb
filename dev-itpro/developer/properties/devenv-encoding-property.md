---
title: "Encoding Property"
description: "Sets a value that specifies which system is applied to the XmlPort for character encoding."
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
# Encoding Property
> **Version**: _Available or changed with runtime version 1.0._

Sets a value that specifies which system is applied to the XmlPort for character encoding.

## Applies to
-   Xml Port

## Property Value

|Value|Available or changed with|Description|
|-----------|-----------|---------------------------------------|
|**UTF8**|runtime version 1.0|Use UTF16 encoding system. This is the default value.|
|**UTF16**|runtime version 1.0|Use UTF16 encoding system.|
|**ISO88592**|runtime version 1.0|Use ISO88592 encoding system.|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Syntax

```AL
Encoding = UTF16;
```
  
## Remarks  

The two options available for this property are UTF8 and UTF16. UTF8 is the default setting. Information about the encoding system used is inserted into the header of the XML document.  
  
## See Also  

[Properties](devenv-properties.md)