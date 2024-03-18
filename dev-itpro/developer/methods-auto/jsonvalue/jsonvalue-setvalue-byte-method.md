---
title: "JsonValue.SetValue(Byte) Method"
description: "Set the contents of the JsonValue variable to the JSON representation of the given value."
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
# JsonValue.SetValue(Byte) Method
> **Version**: _Available or changed with runtime version 1.0._

Set the contents of the JsonValue variable to the JSON representation of the given value.


## Syntax
```AL
 JsonValue.SetValue(Value: Byte)
```
## Parameters
*JsonValue*  
&emsp;Type: [JsonValue](jsonvalue-data-type.md)  
An instance of the [JsonValue](jsonvalue-data-type.md) data type.  

*Value*  
&emsp;Type: [Byte](../byte/byte-data-type.md)  
  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks
- When Value is a Char, Byte, Option, Integer type, the integral value will be stored and serialized as a JSON Number.
- The JsonValue will be disconnected from its current JSON tree and the data contained by the JsonValue will be replaced with the new value.

## See Also
[JsonValue Data Type](jsonvalue-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)