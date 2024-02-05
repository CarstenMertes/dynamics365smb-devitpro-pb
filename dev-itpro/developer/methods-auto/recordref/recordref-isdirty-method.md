---
title: "RecordRef.IsDirty() Method"
description: "Gets a boolean value that indicates whether the current in-memory instance of a record or filtered set of records has changed since being retrieved from the database."
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
# RecordRef.IsDirty() Method
> **Version**: _Available or changed with runtime version 5.0._

Gets a boolean value that indicates whether the current in-memory instance of a record or filtered set of records has changed since being retrieved from the database.


## Syntax
```AL
Dirty :=   RecordRef.IsDirty()
```
> [!NOTE]
> This method can be invoked using property access syntax.

## Parameters
*RecordRef*  
&emsp;Type: [RecordRef](recordref-data-type.md)  
An instance of the [RecordRef](recordref-data-type.md) data type.  

## Return Value
*Dirty*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the a table or filtered set of records has changed; otherwise, **false**.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[RecordRef Data Type](recordref-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)