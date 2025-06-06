---
title: Boolean operators
description: Description of the Boolean operators in AL for Business Central.
ms.reviewer: solsen
ms.topic: concept-article
ms.date: 07/01/2024
ms.author: solsen
author: KennieNP
ms.custom: evergreen
ms.collection: get-started
---

# Boolean (logical) operators

Logical operators can only be used with arguments that can be evaluated to a boolean. The result of a logical operation is a boolean. The following table shows the logical operators that are available in AL.

## Boolean operators

As the following table shows, the `not` operator is a unary prefix operator. This means that it takes only one argument and is placed in front of the argument. The `and`, `or`, and `xor` operators are binary infix operators; they take two arguments and are placed between the corresponding arguments.  

|Operator|Name|Expression|Resulting data type|  
|--------|----|----------|-------------------|  
|`not`|Logical negation|not bool|Boolean|  
|`and`|Logical and|bool1 and bool2|Boolean|  
|`or`|Logical or|bool1 or bool2|Boolean|  
|`xor`|Exclusive logical or|bool1 xor bool2|Boolean|  

## Related information

[AL operators](devenv-al-operators.md)  
[Arithmetic operators](devenv-al-arithmetic-operators.md)  
[Relational operators](devenv-al-relational-operators.md)  
