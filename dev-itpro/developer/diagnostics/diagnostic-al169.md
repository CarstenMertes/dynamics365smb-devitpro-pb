---
title: "Compiler Error AL0169"
description: "The option value '{0}' is not valid."
ms.author: solsen
ms.custom: na
ms.date: 06/10/2022
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Compiler Error AL0169

[!INCLUDE[banner_preview](../includes/banner_preview.md)]

The option value '{0}' is not valid.

## Description
Non-valid option value.  

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Example

```al
enum 100510 myEnum
{
    ObsoleteState = Removed;
    ...
}
```
Setting the ObsoleteState to Removed for an enum will throw the following error:

`The option value ``Removed`` is not valid`

## See Also  
[Get Started with AL](../devenv-get-started.md)  
[Developing Extensions](../devenv-dev-overview.md)  