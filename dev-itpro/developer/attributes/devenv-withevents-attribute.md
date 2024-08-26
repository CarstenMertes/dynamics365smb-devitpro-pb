---
title: "WithEvents attribute"
description: "Sets whether a DotNet variable subscribes to the events published by a .NET Framework type."
ms.author: solsen
ms.date: 08/26/2024
ms.topic: reference
author: SusanneWindfeldPedersen
ms.reviewer: solsen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)

# WithEvents attribute
> **Version**: _Available or changed with runtime version 1.0._

Sets whether a DotNet variable subscribes to the events published by a .NET Framework type.

> [!NOTE]
> This attribute is supported only in Business Central on-premises.

## Applies to

- Variable


## Syntax

```AL
[WithEvents]
```

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

You can only subscribe to events that are emitted by global variables of the .NET type marked with the WithEvents property. For all the global variables that are marked with this property, the compiler will expose the events available on the type as triggers on the variable. The syntax for declaring these triggers is `{VariableName}::{EventName}(...ParameterList)`, but IntelliSense will offer suggestions for the event name and autocomplete the parameter list.

## See Also

[Get Started with AL](../devenv-get-started.md)  
[Developing Extensions](../devenv-dev-overview.md)  