---
title: "Report.Quit() Method"
description: "Aborts the processing of a report or XmlPort."
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
# Report.Quit() Method
> **Version**: _Available or changed with runtime version 1.0._

Aborts the processing of a report or XmlPort.


## Syntax
```AL
 Report.Quit()
```
## Parameters
*Report*  
&emsp;Type: [Report](report-data-type.md)  
An instance of the [Report](report-data-type.md) data type.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  
 When you use the QUIT method, the report or XMLport is exited without committing any changes that were made to the database during the execution. The [OnPostReport Trigger](../../triggers-auto/report/devenv-onpostreport-report-trigger.md) or [OnPostXMLport Trigger](../../triggers-auto/xmlport/devenv-onpostxmlport-xmlport-trigger.md) trigger will not be called.  
  
## Example  
 The following example shows how to use the QUIT method to abort an execution without committing any changes that were made during the processing.  
  
```  
  
// Do some database processing.  
CurrReport.QUIT;  
  
```  

## See Also
[Report Data Type](report-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)