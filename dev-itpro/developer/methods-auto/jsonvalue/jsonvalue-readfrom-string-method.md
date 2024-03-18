---
title: "JsonValue.ReadFrom(Text) Method"
description: "Reads the JSON data into a JsonValue variable."
ms.author: solsen
ms.custom: na
ms.date: 03/24/2022
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# JsonValue.ReadFrom(Text) Method
> **Version**: _Available or changed with runtime version 1.0._

Reads the JSON data into a JsonValue variable.


## Syntax
```AL
[Ok := ]  JsonValue.ReadFrom(Data: Text)
```
## Parameters
*JsonValue*  
&emsp;Type: [JsonValue](jsonvalue-data-type.md)  
An instance of the [JsonValue](jsonvalue-data-type.md) data type.  

*Data*  
&emsp;Type: [Text](../text/text-data-type.md)  
The String object from which the JSON data will be read.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the read was successful; otherwise, **false**. If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks 
This method can fail if the JSON data is malformed.
If the operation succeeds, the JsonValue will be disconnected from its current JSON tree and the data contained by the JsonValue will be replaced with the new value.
To delete the contents in a JsonValue variable use the Clear function.

```
Clear(JsonValue)
```

## Example
This example shows how to read JSON data from a string into a JsonValue variable.

```al
local procedure ReadJson(data : Text) result : JsonValue;
begin
    result.ReadFrom(data);    
end;
```

## See Also
[JsonValue Data Type](jsonvalue-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)