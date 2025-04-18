---
title: "ObsoleteReason property"
description: "Specifies why the object has been marked as Pending in the ObsoleteState property."
ms.author: solsen
ms.date: 02/18/2025
ms.topic: reference
author: SusanneWindfeldPedersen
ms.reviewer: solsen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# ObsoleteReason Property
> **Version**: _Available or changed with runtime version 10.0._

Specifies why the object has been marked as Pending in the ObsoleteState property.

## Applies to
-   Page Action Ref
-   Page Custom Action
-   Page File Upload Action
-   Report Layout
-   Table
-   Table field
-   Table key
-   Codeunit
-   Enum Type
-   Enum Value
-   Page Action
-   Page Action Group
-   Page Action Separator
-   Page Part
-   Page System Part
-   Page Chart Part
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
-   Page Field
-   Page Action Area
-   Page Area
-   Page
-   Page View
-   Profile
-   Interface
-   Control Add In
-   Permission Set
-   Field Group

[//]: # (IMPORTANT: END>DO_NOT_EDIT)


## Syntax

```AL
ObsoleteReason = 'Not Needed';
```

## Remarks 

Use this property to inform developers about an object or element that will become obsolete in time or is already obsolete. Use the [ObsoleteTag Property](devenv-obsoletetag-property.md) to specify additional information which can be valuable to other developers.

## Related information

[ObsoleteState](devenv-obsoletestate-property.md)  
[ObsoleteTag](devenv-obsoletetag-property.md)  
[Properties](devenv-properties.md)  
[MethodType Property (Upgrade Codeunits)](../devenv-methodtype-property-upgrade-codeunits.md)  
[Obsolete Attribute](../attributes/devenv-obsolete-attribute.md)  