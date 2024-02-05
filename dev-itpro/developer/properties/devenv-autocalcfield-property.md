---
title: "AutoCalcField Property"
description: "Sets whether FlowFields should be automatically calculated."
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
# AutoCalcField Property
> **Version**: _Available or changed with runtime version 1.0._

Sets whether FlowFields should be automatically calculated.

## Applies to
-   Xml Port Field Attribute
-   Xml Port Field Element
-   Report Column

[//]: # (IMPORTANT: END>DO_NOT_EDIT)


## Property Value  
 **True** if the FlowField is automatically calculated; otherwise, **false**. The default is **true**.  

## Syntax
```AL
AutoCalcField = false;
```

## Remarks
FlowFields have an effect if the associated data source is a calculated value of the FlowFields.

## See Also  
[FlowFields](../devenv-flowfields.md)   
[Create FlowFields and FlowFilters](../devenv-creating-flowfields-and-flowfilters.md)   
[CalcFormula Property](devenv-calcformula-property.md)  
[FlowFilter Overview](../devenv-flowfilter-overview.md)   
[CalcFields Property](devenv-calcfields-property.md)