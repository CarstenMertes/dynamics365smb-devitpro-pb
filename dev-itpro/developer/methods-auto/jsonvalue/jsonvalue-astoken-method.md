---
title: "JsonValue.AsToken() Method"
description: "Converts the value in a JsonValue to a JsonToken data type."
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
# JsonValue.AsToken() Method
> **Version**: _Available or changed with runtime version 1.0._

Converts the value in a JsonValue to a JsonToken data type.


## Syntax
```AL
Token :=   JsonValue.AsToken()
```

## Parameters
*JsonValue*  
&emsp;Type: [JsonValue](jsonvalue-data-type.md)  
An instance of the [JsonValue](jsonvalue-data-type.md) data type.  

## Return Value
*Token*  
&emsp;Type: [JsonToken](../jsontoken/jsontoken-data-type.md)  
The returned JsonToken contains the same data as the JsonValue, but allows for treating the data in a generic manner.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)



## See Also
[JsonValue Data Type](jsonvalue-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)