---
title: "JsonArray.IndexOf(BigInteger) Method"
description: "Determines the index of a specific value in the JsonArray."
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
# JsonArray.IndexOf(BigInteger) Method
> **Version**: _Available or changed with runtime version 1.0._

Determines the index of a specific value in the JsonArray.


## Syntax
```AL
Index :=   JsonArray.IndexOf(Value: BigInteger)
```
## Parameters
*JsonArray*  
&emsp;Type: [JsonArray](jsonarray-data-type.md)  
An instance of the [JsonArray](jsonarray-data-type.md) data type.  

*Value*  
&emsp;Type: [BigInteger](../biginteger/biginteger-data-type.md)  
  


## Return Value
*Index*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The position of the value in the JsonArray. -1 will be returned if Value cannot be found in the array.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

> [!NOTE]  
> The JsonArray is 0-based by design.

## See Also
[JsonArray Data Type](jsonarray-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)