---
title: "Variant.IsDataClassificationType() Method"
description: "Indicates whether an AL variant contains a DataClassification variable."
ms.author: solsen
ms.custom: na
ms.date: 07/07/2021
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Variant.IsDataClassificationType() Method
> **Version**: _Available or changed with runtime version 1.0 until version 8.0 where it was deprecated for the following reason: "The property IsDataClassificationType is being deprecated. Use the property IsDataClassification instead."_

Indicates whether an AL variant contains a DataClassification variable.


## Syntax
```AL
Ok :=   Variant.IsDataClassificationType()
```
> [!NOTE]
> This method can be invoked using property access syntax.

## Parameters
*Variant*  
&emsp;Type: [Variant](variant-data-type.md)  
An instance of the [Variant](variant-data-type.md) data type.  

## Return Value
*Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the AL variant contains a DataClassification variable, otherwise **false**.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[Variant Data Type](variant-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)