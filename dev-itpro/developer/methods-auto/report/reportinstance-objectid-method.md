---
title: "Report.ObjectId([Boolean]) Method"
description: "Gets or sets the name or number of the report."
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
# Report.ObjectId([Boolean]) Method
> **Version**: _Available or changed with runtime version 1.0._

Gets or sets the name or number of the report.


## Syntax
```AL
String :=   Report.ObjectId([UseNames: Boolean])
```
## Parameters
*Report*  
&emsp;Type: [Report](report-data-type.md)  
An instance of the [Report](report-data-type.md) data type.  

*[Optional] UseNames*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** (default value) if the returned string contains the name of the report, **false** if the returned string contains the number of the report.  


## Return Value
*String*  
&emsp;Type: [Text](../text/text-data-type.md)  
The name or number of the report.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[Report Data Type](report-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)