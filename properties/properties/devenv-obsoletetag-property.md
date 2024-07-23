---
title: "ObsoleteTag Property"
description: "Description of the ObsoleteTag property"
author: SusanneWindfeldPedersen
ms.date: 10/01/2020
ms.suite: na
ms.topic: article
ms.author: solsen
---

# ObsoleteTag Property

Specifies a free-form text to support tracking of where and when the object was marked as obsolete, for example, branch, build, or date of obsoleting the object.

## Applies to  

- Table objects
- Table fields
- Table keys
- Codeunit
- Enum
- EnumValue
- Page
- PageAction
- PageActionArea
- PageActionGroup
- PageActionSeparator
- PageArea
- PageChartPart
- PageField
- PageGroup
- PageLabel
- PagePart
- PageSystemPart
- Query
- QueryColumn
- QueryDataItem
- QueryFilter
- Report
- ReportColumn
- ReportDataItem
- RequestPage
- XmlPort
  
## Property Value  

A free-form text.

## Syntax

```AL
ObsoleteTag = 'This field is being deprecated with the newest build of the product.';
```

## Remarks

Use this property to add valuable information to developers about a table, field, or key that will become obsolete in time or is already obsolete. For procedures and variables, the obsolete tag can be specified as an optional parameter in the `Obsolete` attribute: `[Obsolete(<Reason>,<tag>)]`. For more information, see [Obsolete Attribute](../methods/devenv-obsolete-attribute.md).

## See Also  

[ObsoleteReason](devenv-obsoletereason-property.md)  
[ObsoleteState](devenv-obsoletestate-property.md)  
[Properties](devenv-properties.md)  
[MethodType Property (Upgrade Codeunits)](../devenv-methodtype-property-upgrade-codeunits.md)  
