---
title: "Report.TotalsCausedBy() Method"
description: "Determines which field caused a group total to be calculated."
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
# Report.TotalsCausedBy() Method
> **Version**: _Available or changed with runtime version 1.0 until version 1.0 where it was deprecated._

Determines which field caused a group total to be calculated. This determines which field changed contents and thereby concluded a group.


## Syntax
```AL
FieldNo :=   Report.TotalsCausedBy()
```
## Parameters
*Report*  
&emsp;Type: [Report](report-data-type.md)  
An instance of the [Report](report-data-type.md) data type.  

## Return Value
*FieldNo*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The number of the field that caused the group to end and a group total to be calculated.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[Report Data Type](report-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)