---
title: "ObsoleteTag Property"
description: "Specifies a free-form text to support tracking of where and when the object was marked as obsolete, for example, branch, build, or date of obsoleting the object."
ms.author: solsen
ms.custom: na
ms.date: 08/02/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# ObsoleteTag Property
> **Version**: _Available or changed with runtime version 10.0._

Specifies a free-form text to support tracking of where and when the object was marked as obsolete, for example, branch, build, or date of obsoleting the object.

## Applies to
-   Page Action Ref
-   Page Custom Action
-   Table
-   Table Field
-   Table Key
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
ObsoleteTag = 'This field is being deprecated with the newest build of the product.';
```

## Remarks

Use this property to add valuable information to developers about an object or element that will become obsolete in time or is already obsolete. For procedures and variables, the obsolete tag can be specified as an optional parameter in the `Obsolete` attribute: `[Obsolete('<Reason>','<tag>')]`. For more information, see [Obsolete Attribute](/dynamics365/business-central/dev-itpro/developer/attributes/devenv-obsolete-attribute).

For an elaborate example of deprecating, see [Best Practices for Deprecation of Code in the Base App](../devenv-deprecation-guidelines.md).

## See Also  

[ObsoleteReason](devenv-obsoletereason-property.md)  
[ObsoleteState](devenv-obsoletestate-property.md)  
[Properties](devenv-properties.md)  
[MethodType Property (Upgrade Codeunits)](../devenv-methodtype-property-upgrade-codeunits.md)  
[Obsolete Attribute](../attributes/devenv-obsolete-attribute.md)