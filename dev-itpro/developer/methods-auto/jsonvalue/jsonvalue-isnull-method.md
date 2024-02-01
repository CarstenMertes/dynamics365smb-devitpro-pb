---
title: "JsonValue.IsNull() Method"
description: "Indicates whether the JsonValue contains the JSON value of NULL."
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
# JsonValue.IsNull() Method
> **Version**: _Available or changed with runtime version 1.0._

Indicates whether the JsonValue contains the JSON value of NULL.


## Syntax
```AL
Ok :=   JsonValue.IsNull()
```
> [!NOTE]
> This method can be invoked using property access syntax.

## Parameters
*JsonValue*  
&emsp;Type: [JsonValue](jsonvalue-data-type.md)  
An instance of the [JsonValue](jsonvalue-data-type.md) data type.  

## Return Value
*Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the JsonValue contains the JSON value of NULL; otherwise, **false**


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[JsonValue Data Type](jsonvalue-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)