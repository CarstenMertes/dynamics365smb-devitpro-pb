---
title: "Record.FindSet(Boolean, Boolean) Method"
description: "Finds a set of records in a table based on the current key and filter."
ms.author: solsen
ms.custom: na
ms.date: 06/30/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Record.FindSet(Boolean, Boolean) Method
> **Version**: _Available or changed with runtime version 1.0 until version 11.0 where it was deprecated for the following reason: "This method has been deprecated because the parameter 'UpdateKey' is not used by the runtime. Use the overload without the 'UpdateKey' parameter instead."_

Finds a set of records in a table based on the current key and filter.


## Syntax
```AL
[Ok := ]  Record.FindSet(ForUpdate: Boolean, UpdateKey: Boolean)
```
## Parameters
*Record*  
&emsp;Type: [Record](record-data-type.md)  
An instance of the [Record](record-data-type.md) data type.  

*ForUpdate*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
Set this parameter to true if you want to modify any records in the set; otherwise, set the parameter to false. If you set this parameter to true, then the LockTable method (Record) is immediately run on the table before the records are read. If you set this parameter to false, then you can still modify the records in the set, but these updates will not be performed optimally. The default value is false.
          

*UpdateKey*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
 The `UpdateKey` parameter has been deprecated and will be removed in the future.
          


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the operation was successful; otherwise **false**.   If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[Record Data Type](record-data-type.md)  
[Getting Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)