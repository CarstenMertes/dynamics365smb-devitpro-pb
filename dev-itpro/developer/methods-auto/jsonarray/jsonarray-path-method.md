---
title: "JsonArray.Path() Method"
description: "Retrieves the JSON path of the array relative to the root of its containing tree."
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
# JsonArray.Path() Method
> **Version**: _Available or changed with runtime version 1.0._

Retrieves the JSON path of the array relative to the root of its containing tree.


## Syntax
```AL
Path :=   JsonArray.Path()
```
> [!NOTE]
> This method can be invoked using property access syntax.
## Parameters
*JsonArray*  
&emsp;Type: [JsonArray](jsonarray-data-type.md)  
An instance of the [JsonArray](jsonarray-data-type.md) data type.  

## Return Value
*Path*  
&emsp;Type: [Text](../text/text-data-type.md)  
The path of the array relative to its containing JSON tree. If the object is the root of the JSON tree, the path will be empty.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[JsonArray Data Type](jsonarray-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)