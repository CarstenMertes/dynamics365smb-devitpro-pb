---
title: AL type conversion in expressions
description: Description of how AL types can be converted.
ms.reviewer: solsen
ms.topic: conceptual
ms.date: 02/07/2025
ms.custom: bap-template
author: SusanneWindfeldPedersen
ms.collection: get-started
---

# AL type conversion in expressions

This article describes type conversions in AL expressions. The examples illustrate how the type conversion rules should be used and the effect of the type conversion that the AL compiler performs. The examples are divided into groups corresponding to the data types in AL.

## AL expression statements and type conversion

Consider the following statements.

```al
charVar := 15;               // A char variable
integerVar := 56000;         // An integer variable
Sum := charVar + integerVar;
```

The last statement involves one or two type conversions. The rightmost statement involves the evaluation of the expression `CharVar + integerVar (char + integer)`. In order to evaluate this expression, the first operand (CharVar) must be converted from char to integer. The addition operator then returns an integer result.

If the type of the leftmost variable is declared as, for example, decimal, the result must be converted from integer to decimal before its value can be assigned to `Sum`. Learn more in [Assignment and type conversion](devenv-al-variables.md#assignment-and-type-conversion).

The following examples illustrate the type conversions, which can occur when expressions are evaluated. The following guidelines are used:

- When asked to evaluate an expression of mixed data types, if it's possible, the system always converts at least one of the operands to a more general data type.
- The data types in the two main groups, numbers and strings, can be ranked from "most general" to "least general."

  :::image type="content" source="../media/al-type-conversion.png" alt-text="Two main groups of data types":::

- The most general data types include all the possible values from the less general data types: a decimal is more general than an integer, which is more general than a char.

- Type conversion can occur in some cases even though two operands have the same type.

These rules are illustrated by the following examples.

### Example 1

The following example shows the evaluation of a numeric expression.

```
integer + decimal
```

This expression contains two subexpressions of different data types. Before it can add these two subexpressions, the system must convert the leftmost subexpression to decimal.

```
decimal + decimal
```

When the leftmost subexpression is converted, the expression can be evaluated, and the resulting data type is decimal.

```
decimal + decimal = decimal
```

### Example 2

The following example shows the evaluation of a string expression.

```
text + code
```

This expression contains two subexpressions that must be concatenated. To do this, the system must convert the subexpression of the least general data type (code) to the most general data type (text).

```
text + text
```

When the rightmost subexpression is converted, the expression can be evaluated, and the resulting data type is text.

```
text + text = text
```

## Related information

[AL variables](devenv-al-variables.md#assignment-and-type-conversion)  
