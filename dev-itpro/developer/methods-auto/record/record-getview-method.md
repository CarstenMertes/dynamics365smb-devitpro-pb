---
title: "Record.GetView([Boolean]) Method"
description: "Gets a string that describes the current sort order, key, and filters on a table."
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
# Record.GetView([Boolean]) Method
> **Version**: _Available or changed with runtime version 1.0._

Gets a string that describes the current sort order, key, and filters on a table.


## Syntax
```AL
String :=   Record.GetView([UseNames: Boolean])
```
## Parameters
*Record*  
&emsp;Type: [Record](record-data-type.md)  
An instance of the [Record](record-data-type.md) data type.  

*[Optional] UseNames*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
Indicates whether a reference to the field caption or the field number should be returned. If set to true (default value) or empty, then the returned string contains references to field captions in the table with which the record is associated. If a field doesn't have a caption, then the name is returned. If the parameter is set to false, then field numbers are used instead.  


## Return Value
*String*  
&emsp;Type: [Text](../text/text-data-type.md)  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[Record Data Type](record-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)