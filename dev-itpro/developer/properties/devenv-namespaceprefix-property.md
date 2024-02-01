---
title: "NamespacePrefix Property"
description: "Specifies the namespace prefix on an XmlPort element."
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
# NamespacePrefix Property
> **Version**: _Available or changed with runtime version 1.0._

Specifies the namespace prefix on an XmlPort element.

## Applies to
-   Xml Port Text Element
-   Xml Port Field Element
-   Xml Port Table Element
-   Xml Port Field Attribute
-   Xml Port Text Attribute

[//]: # (IMPORTANT: END>DO_NOT_EDIT)


## Syntax

```AL
NamespacePrefix = 'bc';
```
 
## Remarks

You can only set the property to a prefix that is declared in the [Namespaces Property](devenv-namespaces-property.md) of the XMLport.  

This property only applies to element node types and will be ignored if it is set in `textattribute` and `fieldattribute` nodes. 

For more information about using namespaces with XMLports, see  [Using Namespaces with XMLports](../devenv-using-namespaces-with-xmlports.md).  

## See Also  

[Get Started with AL](../devenv-get-started.md)  
[Developing Extensions](../devenv-dev-overview.md)  