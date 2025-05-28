---
title: Preprocessor directives in AL
description: The different types of preprocessor directives in AL; conditional, regions, and pragmas and preprocessorSymbols setting.
author: SusanneWindfeldPedersen
ms.date: 03/19/2024
ms.topic: article
ms.author: solsen
ms.reviewer: solsen
---

# Preprocessor directives in AL

[!INCLUDE[2020_releasewave2](../../includes/2020_releasewave2.md)]

In AL, like in other programming languages, preprocessor directives can be used to make code conditional, to suppress warnings, or to enable the ability to expand and collapse in code. Preprocessor directives can be divided into the following groups. For more information about each type, use the links provided in the following section.

- [Conditional directives](devenv-directives-in-al.md#conditional-directives)
- [Regions](devenv-directive-region.md)
- [Pragmas](devenv-directive-pragma.md)

Any code can be made conditional, including table fields, and checked using a conditional directive. To check code using a conditional directive, you must define a symbol to check. A symbol returns a boolean value: `true` or `false`. Symbols can be defined at the beginning of a source file, where the scope of the specific symbol is in the file in which it is defined. You can also define symbols in the `app.json` file, and then the scope is global for the extension.

> [!NOTE]  
> Built-in symbols are currently not supported in AL. Symbols must be defined in a specific file or in the `app.json` file.

> [!NOTE]  
> User personalization and profile configuration (including profile copy) are not meant to work with directives, which means that they are ignored by the platform in the cases of #pragma, #region, #endregion and fail with an error when they are not supported for #if, #elif, #define, etc.

## Conditional directives

The following conditional preprocessor directives are supported in AL.

|Conditional preprocessor directive |Description |
|-----------------------|------------|
|#if                    | Specifies the beginning of a conditional clause. The `#endif` clause ends it. Compiles the code between the directives if the specified symbol being checked is defined. <br><br>  Inside the `#if` directive, you can use logical operators to create complex conditions. The supported logical operators are shown in the [next section](#logical-operators-in-conditional-directives). |
|#else                  | Specifies a compound conditional clause. If none of the preceding clauses evaluate to `true`, the compiler will evaluate code between `#else` and `#endif`. |
|#elif                  | Combines `else` and `if`. If `#elif` is `true` the compiler evaluates all code between `#elif` and the next conditional directive.|
|#endif                 | Specifies the end of a conditional clause that begins with `#if`. |
|#define                | Defines a symbol that can be used to specify conditions for a compilation. For example, `#define DEBUG`. The scope of the symbol is the file that it was defined in.|
|#undef                 | Undefines a symbol. |

### Logical operators in conditional directives

The operators `and`, `or`, and `not` are supported in conditional directives. `and` evaluates to `true` if both operands are true, `or` evaluates to `true` if at least one of the operands is true, and `not` negates the value of the operand.

## Defining preprocessorSymbols

Symbols can be defined globally in the `app.json` file. A symbol can also be defined using the `#define` directive in code, but if symbols are defined in the `app.json` file, they can be used globally. The following example defines `DEBUG` as a global symbol. This can then be used from code as illustrated in the following [Conditional code](devenv-directives-in-al.md#conditional-directives) example. A symbol has a boolean value that means it evaluates to `true` or `false`.

The app.json syntax is:

```json
"preprocessorSymbols": [name [,name2]]
```

For example:

```json
"preprocessorSymbols": [ "DEBUG","PROD"]
```

For more information, see [JSON Files](../devenv-json-files.md).

## Example

```AL
#if DEBUG
    trigger OnOpenPage()
    begin
        Message('Only in debug versions');
    end;
#endif

```

## Related information

[Development in AL](../devenv-dev-overview.md)  
[AL development environment](../devenv-reference-overview.md)  
[Conditional directives](devenv-directives-in-al.md#conditional-directives)  
[Region directive in AL](devenv-directive-region.md)  
[Pragma directive in AL](devenv-directive-pragma.md)  
[Deprecating explicit and implicit with statements](../devenv-deprecating-with-statements-overview.md)  
[Best practices for deprecation of code in the Base App](../devenv-deprecation-guidelines.md)  
[ObsoleteState property](../properties/devenv-obsoletestate-property.md)  
[ObsoleteReason property](../properties/devenv-obsoletereason-property.md)  
[ObsoleteTag property](../properties/devenv-obsoletetag-property.md)  
[Obsolete attribute](../attributes/devenv-obsolete-attribute.md)  
