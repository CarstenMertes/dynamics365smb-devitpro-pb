---
title: "XmlVersionNo Property"
description: "Set which version of XML the XML document conforms to."
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
# XmlVersionNo Property
> **Version**: _Available or changed with runtime version 1.0._

Set which version of XML the XML document conforms to. Two options are available: 1.0 (the default) and 1.1.

## Applies to
-   Xml Port

## Property Value

|Value|Available or changed with|Description|
|-----------|-----------|---------------------------------------|
|**V10**|runtime version 1.0|Version 1.0. This is the default value.|
|**V11**|runtime version 1.0|Version 1.1.|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)


## Syntax

```AL
XMLVersionNo = V10;
```
  
## Remarks

The XML version number is inserted into the XML document as the XML declaration.  
  
## See Also  

[Properties](devenv-properties.md)