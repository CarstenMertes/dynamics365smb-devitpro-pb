---
title: "Session.LogMessage(Text, Text, Verbosity, DataClassification, TelemetryScope, Dictionary of [Text, Text]) Method"
description: "Logs a trace message to a telemetry account."
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
# Session.LogMessage(Text, Text, Verbosity, DataClassification, TelemetryScope, Dictionary of [Text, Text]) Method
> **Version**: _Available or changed with runtime version 5.4._

Logs a trace message to a telemetry account.


## Syntax
```AL
 Session.LogMessage(EventId: Text, Message: Text, Verbosity: Verbosity, DataClassification: DataClassification, TelemetryScope: TelemetryScope, CustomDimensions: Dictionary of [Text, Text])
```
> [!NOTE]
> This method can be invoked without specifying the data type name.
## Parameters
*EventId*  
&emsp;Type: [Text](../text/text-data-type.md)  
The event ID of trace message.  

*Message*  
&emsp;Type: [Text](../text/text-data-type.md)  
The message logged into telemetry.  

*Verbosity*  
&emsp;Type: [Verbosity](../verbosity/verbosity-option.md)  
The verbosity of the log.  

*DataClassification*  
&emsp;Type: [DataClassification](../dataclassification/dataclassification-option.md)  
Classification of data in message.  

*TelemetryScope*  
&emsp;Type: [TelemetryScope](../telemetryscope/telemetryscope-option.md)  
Specifies the scope of this trace message:
- ExtensionPublisher: Will emit this trace message to the Extension Publisher's telemetry account.
- All: Will emit this trace message additionally to the Partner's telemetry account.  

*CustomDimensions*  
&emsp;Type: [Dictionary of [Text, Text]](../dictionary/dictionary-data-type.md)  
Set of additional dimensions, specified as a dictionary, that will be emitted to the telemetry account and that can be used to specify filters in the query.  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

For more information about using this method, see [Creating Custom Telemetry Events for Application Insights](../../devenv-instrument-application-for-telemetry-app-insights.md).

## Example

```al
trigger OnRun();
var
    CustomDimensions: Dictionary of [Text, Text];
begin
    CustomDimensions.Add('result', 'failed');
    CustomDimensions.Add('reason', 'critical error in code');
    CustomDimensions.Add('alCallstack', "Error Message Management".GetCurrCallStack());    
    LogMessage('MyExt-0001', 'This is a critical error message', Verbosity::Normal, DataClassification::SystemMetadata, TelemetryScope::ExtensionPublisher, CustomDimensions);
end;
```

## See Also
[Session Data Type](session-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)
