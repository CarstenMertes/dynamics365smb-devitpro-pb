---
title: "Label Data Type"
description: "Denotes a string constant that can be optionally translated into multiple languages."
ms.author: solsen
ms.custom: na
ms.date: 05/11/2021
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Label Data Type
> **Version**: _Available or changed with runtime version 1.0._

Denotes a string constant that can be optionally translated into multiple languages.




[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Parameters

All of the parameters below are *optional* and the order is not enforced.

| Attribute   | Description|
|-------------|--------------|
|**Comment**  | Used for general comments about the label, specifically about the placeholders in that label.|
|**Locked**   | When Locked is set to **true**, the label should not be translated. Default value is **false**.|
|**MaxLength**| Determines how much of the label is used.</br> `<br>If no maximum length is specified, the string can be any length.|

## Syntax example

```al
var
    a : Label 'Label Text', Comment='Foo', MaxLength=999, Locked=true;
```

## Remarks

The `Label` data type is used in .xlf files for translations. For more information, see [Working with Translation Files](../../devenv-work-with-translation-files.md). 

For information about naming, see [CodeCop Rule AA0074](../../analyzers/codecop-aa0074.md).

## See Also

[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  