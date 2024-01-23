---
title: "Report.GetSubstituteReportId(Integer) Method"
description: "Gets the ID of the report that will be run by the platform after considering any substitutions made by extensions."
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
# Report.GetSubstituteReportId(Integer) Method
> **Version**: _Available or changed with runtime version 2.0._

Gets the ID of the report that will be run by the platform after considering any substitutions made by extensions.


## Syntax
```AL
NewReportId :=   Report.GetSubstituteReportId(ReportId: Integer)
```
## Parameters
*ReportId*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The ID of the report for which you want to retrieve the ID of the possible report substitute.  


## Return Value
*NewReportId*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The ID of the report that will be run by the platform after considering any substitutions made by extensions.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remark
If no object exists with the integer supplied in the _Report.GetSubstituteReportId(Integer)_ method, the method won't fail. Instead, the method will just return the supplied integer.


## See Also
[Substituting Reports](../../devenv-substituting-reports.md)  
[Report Data Type](report-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)
