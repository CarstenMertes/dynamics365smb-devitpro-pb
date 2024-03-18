---
title: "JsonValue.AsCode() Method"
description: "Converts the value in a JsonValue to a Code data type."
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
# JsonValue.AsCode() Method
> **Version**: _Available or changed with runtime version 1.0._

Converts the value in a JsonValue to a Code data type.


## Syntax
```AL
Result :=   JsonValue.AsCode()
```

## Parameters
*JsonValue*  
&emsp;Type: [JsonValue](jsonvalue-data-type.md)  
An instance of the [JsonValue](jsonvalue-data-type.md) data type.  

## Return Value
*Result*  
&emsp;Type: [Code](../code/code-data-type.md)  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks
The operation will fail with a run-time error if the JsonValue contains NULL or UNDEFINED.

## See Also
[JsonValue Data Type](jsonvalue-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)