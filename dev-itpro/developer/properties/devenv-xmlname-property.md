---
title: "XmlName Property"
description: "Sets a variable name for the table or the text that is the data source of the current element."
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
# XmlName Property
> **Version**: _Available or changed with runtime version 1.0._

Sets a variable name for the table or the text that is the data source of the current element.

## Applies to
-   Xml Port Text Element
-   Xml Port Field Element
-   Xml Port Table Element
-   Xml Port Field Attribute
-   Xml Port Text Attribute

[//]: # (IMPORTANT: END>DO_NOT_EDIT)


## Property Value

String

## Syntax

```AL
XmlName = 'CreditNote';
```

## Remarks

If the **XmlName** property is not defined, it will use the string specified in the [NodeName Property](./devenv-properties.md) as the default variable name.

## See Also  

[Properties](devenv-properties.md)