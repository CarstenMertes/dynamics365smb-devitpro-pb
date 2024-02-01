---
title: "Report.Print(Text [, Text] [, RecordRef]) Method"
description: "Prints a specified report without running the request page."
ms.author: solsen
ms.custom: na
ms.date: 03/02/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Report.Print(Text [, Text] [, RecordRef]) Method
> **Version**: _Available or changed with runtime version 1.0._

Prints a specified report without running the request page. Instead of using the request page to obtain parameters at runtime, the method gets the parameter values as an input parameter string, typically from a RUNREQUESTPAGE method call.

> [!NOTE]
> From runtime version 9.0 and onward, this method is supported in Business Central online.

## Syntax
```AL
 Report.Print(Parameters: Text [, PrinterName: Text] [, RecordRef: RecordRef])
```
## Parameters
*Report*  
&emsp;Type: [Report](report-data-type.md)  
An instance of the [Report](report-data-type.md) data type.  

*Parameters*  
&emsp;Type: [Text](../text/text-data-type.md)  
A string of request page parameters as XML to use to run the report. The parameter string is typically retrieved from the return value a RUNREQUESTPAGE method call.  

*[Optional] PrinterName*  
&emsp;Type: [Text](../text/text-data-type.md)  
The name of the printer to use to print the report. The printer must be set up on the client computer. If you do not set this variable, the printer that is set as the default printer is used.  

*[Optional] RecordRef*  
&emsp;Type: [RecordRef](../recordref/recordref-data-type.md)  
The RecordRef that refers to the table in which you want to find a record.  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  
 You typically use this method together with the [RunRequestPage Method](../../methods-auto/report/report-runrequestpage-method.md) method. The RunRequestPage method runs a report request page without actually running the report, but instead, returns the parameters that are set on the request page as a string. You can then call the Print method to get the parameter string and print the report.  

 For a simple example that illustrates how to use the Print method, see example in the [RunRequestPage Method](../../methods-auto/report/report-runrequestpage-method.md) method topic.  
## See Also
[Report Data Type](report-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)