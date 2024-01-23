---
title: "RecordRef.Mark([Boolean]) Method"
description: "Marks a record."
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
# RecordRef.Mark([Boolean]) Method
> **Version**: _Available or changed with runtime version 5.3._

Marks a record. You can also use this method to determine whether a record is marked.


## Syntax
```AL
[Marked := ]  RecordRef.Mark([Mark: Boolean])
```
## Parameters
*RecordRef*  
&emsp;Type: [RecordRef](recordref-data-type.md)  
An instance of the [RecordRef](recordref-data-type.md) data type.  

*[Optional] Mark*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
Specifies if a record is marked.  


## Return Value
*[Optional] Marked*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the record is marked; otherwise, **false**.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[RecordRef Data Type](recordref-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)