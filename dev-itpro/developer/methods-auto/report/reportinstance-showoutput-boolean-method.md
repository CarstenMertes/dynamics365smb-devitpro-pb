---
title: "Report.ShowOutput(Boolean) Method"
description: "Returns the current setting of whether a section should be printed, and changes this setting."
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
# Report.ShowOutput(Boolean) Method
> **Version**: _Available or changed with runtime version 2.3 until version 2.3 where it was deprecated._

Returns the current setting of whether a section should be printed, and changes this setting.


## Syntax
```AL
[Show := ]  Report.ShowOutput(Value: Boolean)
```
> [!NOTE]
> This method can be invoked using property access syntax.
## Parameters
*Report*  
&emsp;Type: [Report](report-data-type.md)  
An instance of the [Report](report-data-type.md) data type.  

*Value*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the section is printed, otherwise **false**.  


## Return Value
*[Optional] Show*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the section is printed, otherwise **false**.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[Report Data Type](report-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)