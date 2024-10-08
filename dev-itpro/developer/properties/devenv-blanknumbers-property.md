---
title: "BlankNumbers property"
description: "Indicates whether the system will clear a range of numbers as it formats them."
ms.author: solsen
ms.date: 08/26/2024
ms.topic: reference
author: SusanneWindfeldPedersen
ms.reviewer: solsen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# BlankNumbers Property
> **Version**: _Available or changed with runtime version 1.0._

Indicates whether the system will clear a range of numbers as it formats them.

## Applies to
-   Table field
-   Page Field

## Property value

|Value|Available or changed with|Description|
|-----------|-----------|---------------------------------------|
|**DontBlank**|runtime version 1.0|Not clear any numbers. This is the default value.|
|**BlankNeg**|runtime version 1.0|Clear negative numbers.|
|**BlankNegAndZero**|runtime version 1.0|Clear negative numbers and zero.|
|**BlankZero**|runtime version 1.0|Clear numbers equal to zero.|
|**BlankZeroAndPos**|runtime version 1.0|Clear positive numbers and zero.|
|**BlankPos**|runtime version 1.0|Clear positive numbers.|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Syntax  
```AL
BlankNumbers = BlankNegAndZero;
```

## Related information  
 [BlankZero Property](devenv-blankzero-property.md)