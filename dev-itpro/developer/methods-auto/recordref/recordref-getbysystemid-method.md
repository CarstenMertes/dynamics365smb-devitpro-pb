---
title: "RecordRef.GetBySystemId(Guid) Method"
description: "Gets a record based on the ID of the record."
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
# RecordRef.GetBySystemId(Guid) Method
> **Version**: _Available or changed with runtime version 4.3._

Gets a record based on the ID of the record. The RecordRef must already be opened.


## Syntax
```AL
[Ok := ]  RecordRef.GetBySystemId(SystemId: Guid)
```
## Parameters
*RecordRef*  
&emsp;Type: [RecordRef](recordref-data-type.md)  
An instance of the [RecordRef](recordref-data-type.md) data type.  

*SystemId*  
&emsp;Type: [Guid](../guid/guid-data-type.md)  
The systemid which uniquely identifies the record that you want to get.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the operation was successful; otherwise **false**.   If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[RecordRef Data Type](recordref-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)