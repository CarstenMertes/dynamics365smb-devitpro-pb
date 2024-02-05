---
title: "Report.Print(Integer, Text [, Text] [, RecordRef]) Method"
description: "Prints a specified report without running the request page."
ms.author: solsen
ms.custom: na
ms.date: 10/25/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Report.Print(Integer, Text [, Text] [, RecordRef]) Method
> **Version**: _Available or changed with runtime version 1.0._

Prints a specified report without running the request page. Instead of using the request page to obtain parameters at runtime, the method gets the parameter values as an input parameter string, typically from a RUNREQUESTPAGE method call.


## Syntax
```AL
 Report.Print(Number: Integer, Parameters: Text [, PrinterName: Text] [, RecordRef: RecordRef])
```
## Parameters
*Number*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The ID of the report that you want to print. If the report that you specify does not exist, then a run-time error occurs.  

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
You typically use this method together with the [RunRequestPage Method](../../methods-auto/report/report-runrequestpage-method.md). The RunRequestPage method runs a report request page without actually running the report, but instead, it returns the parameters that are set on the request page as a string. You can then call the Print method to get the parameter string and print the report.  

> [!NOTE]  
> Be careful when crafting the string for the RunRequestPage parameter without using the RunRequestPage method. If the XML content is malformed, then a runtime error might occur when calling `Report.Execute`. 

> [!NOTE]  
> If no default printer has been set up, or if the printer supplied in the **PrinterName** parameter doesn't exist, a PDF version of the document is downloaded to the client.  

> [!NOTE]  
> The `Report.Print` method isn't supported for reports running with an Excel Layout.


## Example (end-to-end scenario)
For a simple example that illustrates how to use the Print method, see example in the [RunRequestPage Method](../../methods-auto/report/report-runrequestpage-method.md) topic. 

## Example (using `Report::<object identifier>` syntax)
As mentioned above, the `Report.Print` method will throw a runtime error if no report with the supplied object ID exists. If you know the report object, a safe way to call `Report.Print` is to use the `Report::<object identifier>` syntax as the compiler will tell you if the report object doesn't exist.  

```AL
procedure PrintKnownReport()
var
    RequestPagePayload: Text;
begin
    RequestPagePayload := Report.RunRequestPage(Report::MyReport);
    Report.Print(Report::MyReport, RequestPagePayload);
end;
```

## See also
[Report Data Type](report-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)
