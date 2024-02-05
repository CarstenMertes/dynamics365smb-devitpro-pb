---
title: "JsonToken.ReadFrom(Text) Method"
description: "Reads the JSON data from the string into a JsonToken variable."
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
# JsonToken.ReadFrom(Text) Method
> **Version**: _Available or changed with runtime version 1.0._

Reads the JSON data from the string into a JsonToken variable.


## Syntax
```AL
[Ok := ]  JsonToken.ReadFrom(String: Text)
```
## Parameters
*JsonToken*  
&emsp;Type: [JsonToken](jsontoken-data-type.md)  
An instance of the [JsonToken](jsontoken-data-type.md) data type.  

*String*  
&emsp;Type: [Text](../text/text-data-type.md)  
The String object from which the JSON data will be read.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the read was successful; otherwise, **false**. If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks
This method can fail if the JSON data is malformed.
If the operation succeeds, the JsonToken will be disconnected from its current JSON tree and the data contained by the JsonToken will be replaced with the new value.
To delete the contents in a JsonToken variable use the Clear function.

```
Clear(JsonToken)
```

## Example
This example shows how to read JSON data from a string into a JsonToken variable.

```al
local procedure ReadJson(data : Text) result : JsonToken;
begin
    result.ReadFrom(data);    
end;
```

## See Also
[JsonToken Data Type](jsontoken-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)