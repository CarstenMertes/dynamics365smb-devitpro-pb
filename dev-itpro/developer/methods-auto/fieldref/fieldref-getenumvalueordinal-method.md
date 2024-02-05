---
title: "FieldRef.GetEnumValueOrdinal(Integer) Method"
description: "Gets the Enum value (or Option member) ordinal value from the Enum metadata for the field that is currently selected."
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
# FieldRef.GetEnumValueOrdinal(Integer) Method
> **Version**: _Available or changed with runtime version 4.0._

Gets the Enum value (or Option member) ordinal value from the Enum metadata for the field that is currently selected.


## Syntax
```AL
The Enum value ordinal value :=   FieldRef.GetEnumValueOrdinal(Index: Integer)
```
## Parameters
*FieldRef*  
&emsp;Type: [FieldRef](fieldref-data-type.md)  
An instance of the [FieldRef](fieldref-data-type.md) data type.  

*Index*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The index in the list of Enum ordinal values to get the Enum value (or Option member) ordinal value for. The index is 1-based.  


## Return Value
*The Enum value ordinal value*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The ordinal value.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[FieldRef Data Type](fieldref-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)