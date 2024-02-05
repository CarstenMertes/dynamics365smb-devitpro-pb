---
title: "Report.IsReadOnly() Method"
description: "Gets if the current report's data access intent is readonly."
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
# Report.IsReadOnly() Method
> **Version**: _Available or changed with runtime version 7.0._

Gets if the current report's data access intent is readonly.


## Syntax
```AL
DataAccessIntent :=   Report.IsReadOnly()
```
> [!NOTE]
> This method can be invoked using property access syntax.
## Parameters
*Report*  
&emsp;Type: [Report](report-data-type.md)  
An instance of the [Report](report-data-type.md) data type.  

## Return Value
*DataAccessIntent*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
A value specifying the readonly data access intent.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[Report Data Type](report-data-type.md)
[Get Started with AL](../../devenv-get-started.md)
[Developing Extensions](../../devenv-dev-overview.md)  