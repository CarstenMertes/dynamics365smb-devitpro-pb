---
title: "Pragma ImplicitWith Directive in AL"
description: "The pragma implicitwith instruction on the pragma directive in AL"
author: SusanneWindfeldPedersen
ms.custom: na
ms.date: 04/01/2021
ms.topic: conceptual
ms.author: solsen
---

# Pragma ImplicitWith

[!INCLUDE[2020_releasewave2](../../includes/2020_releasewave2.md)]

The `#pragma implicitwith` instruction changes the compiler behavior to not create an implicit `with`. This can be used as a temporary solution to avoid getting warnings on the usage of implicit `with` statements in the code, that you plan on rewriting but just haven't fixed yet. With the `#pragma implicitwith disable`, you disable the emit of implicit `with` warnings for a specific location in code that follows the instruction, and with `#pragma implicitwith restore` you restore the warning back to its original state. If you don't `restore`, the `disable` instruction is valid for the rest of the file.

In the `app.json` file, you can set the `NoImplicitWith` flag to disable implicit `with` when you've rewritten all code. For more information, see [JSON Files](../devenv-json-files.md#appjson-file).

> [!NOTE]  
> With [!INCLUDE[prod_short](../../includes/prod_short.md)] 2022 release wave 2, the **AL:Go!** template for creating new AL projects in Visual Studio Code, now enables explicit `with` statements by default, by adding the `NoImplicitWith` option to the `features` property in the generated app.json file.

> [!IMPORTANT]  
> It's important to be aware that the `implicitwith` warning will become an error in a future release and therefore suppressing it should be a temporary solution. It's recommended to rewrite code as described in [Deprecating Explicit and Implicit With Statements](../devenv-deprecating-with-statements-overview.md).

## Syntax

```AL
#pragma implicitwith disable
```

```AL
#pragma implicitwith restore
```

## Example

For more background information and examples, see [Deprecating Explicit and Implicit With Statements](../devenv-deprecating-with-statements-overview.md).

## See Also

[Development in AL](../devenv-dev-overview.md)  
[AL Development Environment](../devenv-reference-overview.md)  
[Pragma Directive in AL](devenv-directive-pragma.md)  
[Conditional directives](devenv-directives-in-al.md#conditional-directives)  
[Deprecating Explicit and Implicit With Statements](../devenv-deprecating-with-statements-overview.md)