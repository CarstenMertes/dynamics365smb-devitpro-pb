---
title: "JsonArray.Set(Integer, JsonValue) Method"
description: "Replaces the value at the given index with a new value."
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
# JsonArray.Set(Integer, JsonValue) Method
> **Version**: _Available or changed with runtime version 1.0._

Replaces the value at the given index with a new value.


## Syntax
```AL
[Ok := ]  JsonArray.Set(Index: Integer, Result: JsonValue)
```
## Parameters
*JsonArray*  
&emsp;Type: [JsonArray](jsonarray-data-type.md)  
An instance of the [JsonArray](jsonarray-data-type.md) data type.  

*Index*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
  
*Result*  
&emsp;Type: [JsonValue](../jsonvalue/jsonvalue-data-type.md)  
  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the read was successful; otherwise, **false**. If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

> [!NOTE]  
> The JsonArray is 0-based by design.

## See Also
[JsonArray Data Type](jsonarray-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)