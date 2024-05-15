---
title: "NamespacePrefix Property"
ms.date: 10/01/2020
ms.suite: na
ms.topic: article
ms.assetid: 1e0022d4-97e7-4bed-9cf9-e07e43d8ad85
caps.latest.revision: 5
author: SusanneWindfeldPedersen
---

# NamespacePrefix Property

Specifies the namespace prefix on an XMLport element.  
  
## Applies to  
  
- Table elements, Field elements and Text elements in XMLports that have the [Format Property (XMLports)](devenv-format-xmlports-property.md) set to **Xml**.  

## Syntax

```AL
NamespacePrefix = 'bc';
```
 
## Remarks

You can only set the property to a prefix that is declared in the [Namespaces Property](devenv-namespaces-property.md) of the XMLport.  

This property only applies to element node types and will be ignored if it is set in `textattribute` and `fieldattribute` nodes. 

For more information about using namespaces with XMLports, see  [Using Namespaces with XMLports](../devenv-using-namespaces-with-xmlports.md).  

## See Also

[Properties](devenv-properties.md)  
[Namespaces Property](devenv-namespaces-property.md)  
[DefaultNamespace Property](devenv-defaultnamespace-property.md)  
[UseDefaultNamespace Property](devenv-usedefaultnamespace-property.md)
