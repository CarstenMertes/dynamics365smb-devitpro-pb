---
title: "JsonArray.Get(Integer, var JsonToken) Method"
description: "Retrieves the value at the given index in the JsonArray."
ms.author: solsen
ms.custom: na
ms.date: 03/02/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# JsonArray.Get(Integer, var JsonToken) Method
> **Version**: _Available or changed with runtime version 1.0._

Retrieves the value at the given index in the JsonArray.


## Syntax
```AL
[Ok := ]  JsonArray.Get(Index: Integer, var Result: JsonToken)
```
## Parameters
*JsonArray*  
&emsp;Type: [JsonArray](jsonarray-data-type.md)  
An instance of the [JsonArray](jsonarray-data-type.md) data type.  

*Index*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The index of the element in the JsonArray that you want to retrieve.  

*Result*  
&emsp;Type: [JsonToken](../jsontoken/jsontoken-data-type.md)  
A variable of type JsonToken that will contain the result if the operation is successful.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the operation was successful; otherwise **false**.   If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

> [!NOTE]  
> The JsonArray is 0-based by design.

The operation will fail if the Index is smaller than 0 or greater or equal than JsonArray.Count.

## See Also
[JsonArray Data Type](jsonarray-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)