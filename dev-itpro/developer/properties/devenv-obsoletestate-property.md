---
title: "ObsoleteState Property"
description: "Marks whether the object will be deprecated."
ms.author: solsen
ms.custom: na
ms.date: 08/04/2022
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# ObsoleteState Property
> **Version**: _Available or changed with runtime version 10.0._

Marks whether the object will be deprecated.

## Applies to
-   Page Action Ref
-   Page Custom Action
-   Table Field
-   Table
-   Table Key
-   Codeunit
-   Enum Type
-   Enum Value
-   Page Action
-   Page Action Area
-   Page Action Group
-   Page Action Separator
-   Page Area
-   Page Part
-   Page System Part
-   Page Chart Part
-   Page Field
-   Page Group
-   Page Label
-   Query
-   Query Column
-   Query Filter
-   Report
-   Report Data Item
-   Report Column
-   Request Page
-   Xml Port
-   Page
-   Page View
-   Profile
-   Interface
-   Control Add In
-   Permission Set
-   Field Group

## Property Value

|Value|Description|
|-----------|---------------------------------------|
|**No**|Not obsolete. This is the normal/default setting.|
|**Pending**|Will become obsolete in a future version.|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)


## Syntax

```AL
ObsoleteState = Pending;
```

## Remarks

By coding against this property, you can use this property as a way to communicate through code to other developers which objects and elements will become obsolete over time and those which are already obsolete, enabling them to adjust their application code accordingly.

> [!NOTE]  
> For all elements, except for **Tables** and **Table fields**, setting `ObsoleteState = Removed` will throw [Compiler Error AL0169](../diagnostics/diagnostic-al169.md) because after an appropriate warning state of `Pending`, these elements can be deleted.

> [!NOTE]  
> When developing using [!INCLUDE[nav_dev_long_md](../includes/nav_dev_long_md.md)] (C/SIDE), you do not get warnings or errors when you compile objects that reference table objects, fields, or keys that are marked as **Pending** or **Removed**. **ObsoleteState** property is only detected by the AL compiler, which will return warnings for references to elements marked as **Pending** and errors for references to elements marked as **Removed**.

## See Also

[ObsoleteReason Property](devenv-obsoletereason-property.md)  
[Properties](devenv-properties.md)  
[Upgrade Codeunits](../devenv-methodtype-property-upgrade-codeunits.md)  
[Obsolete Attribute](../attributes/devenv-obsolete-attribute.md)  