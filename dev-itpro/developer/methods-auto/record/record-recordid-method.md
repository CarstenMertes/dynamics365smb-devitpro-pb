---
title: "Record.RecordId() Method"
description: "Gets the RecordId of the record that is currently selected in the table."
ms.author: solsen
ms.custom: na
ms.date: 07/13/2021
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Record.RecordId() Method
> **Version**: _Available or changed with runtime version 1.0._

Gets the RecordId of the record that is currently selected in the table. If no table is selected, an error is generated.


## Syntax
```AL
RecordID :=   Record.RecordId()
```
> [!NOTE]
> This method can be invoked using property access syntax.

## Parameters
*Record*  
&emsp;Type: [Record](record-data-type.md)  
An instance of the [Record](record-data-type.md) data type.  

## Return Value
*RecordID*  
&emsp;Type: [RecordId](../recordid/recordid-data-type.md)  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[Record Data Type](record-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)