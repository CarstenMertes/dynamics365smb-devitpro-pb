---
title: "AssignmentCompatibility Property"
description: "Sets whether an Enum can be assigned to from another Enum type."
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
# AssignmentCompatibility Property
> **Version**: _Available or changed with runtime version 5.0._

Sets whether an Enum can be assigned to from another Enum type. This is intended for backwards compatibility when splitting existing Options into multiple Enums.

## Applies to
-   Enum Type

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

The default value of this property is `false`.

> [!IMPORTANT]  
> This property provides backwards compatibility in certain cases when converting from options to enums. It should not be used for enums that are not converted from options. 
> Because the assignment is done by ordinal value without validation, there is no guarantee that the target will have a corresponding value. Special attention should be made if either source or target is marked as `extensible`.


## Syntax

```AL
AssignmentCompatibility = true;
```


## See Also
[Extensible Enums](../devenv-extensible-enums.md)  