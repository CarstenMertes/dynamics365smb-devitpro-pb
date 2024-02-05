---
title: "Record.ClearMarks() Method"
description: "Removes all the marks from a record."
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
# Record.ClearMarks() Method
> **Version**: _Available or changed with runtime version 1.0._

Removes all the marks from a record.


## Syntax
```AL
 Record.ClearMarks()
```

## Parameters
*Record*  
&emsp;Type: [Record](record-data-type.md)  
An instance of the [Record](record-data-type.md) data type.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Example

```al
    var
        CustomerRec: Record Customer;
    begin
        CustomerRec.ClearMarks;
    end;
```  

## See Also
[Record Data Type](record-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)