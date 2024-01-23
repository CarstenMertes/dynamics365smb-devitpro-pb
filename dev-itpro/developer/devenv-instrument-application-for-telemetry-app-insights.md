---
title: Creating custom telemetry signals for Application Insights
description: This article describes how to add code to application objects that enables you to gather telemetry.
ms.custom: na
ms.date: 04/01/2021
ms.reviewer: na
ms.topic: conceptual
author: jswymer
---
# Creating Custom Telemetry Traces for Application Insights Monitoring

[!INCLUDE[2020_releasewave2](../includes/2020_releasewave2.md)]

[!INCLUDE[azure-ad-to-microsoft-entra-id](~/../shared-content/shared/azure-ad-to-microsoft-entra-id.md)]

This article explains how to develop extensions to send custom telemetry trace signals to Azure Application Insights for viewing and analyzing.

You can add AL code in extensions to emit messages about activities or operations that users do within the application. At runtime, the messages can be picked up by an Application Insights resource, which you set up beforehand. In Application Insights, the custom telemetry events are stored in the *traces* table.   

## Set up Application Insights 

An Application Insights resource can be configured in two places:

- In the app.json file of the extension.

    For more information, see [Enabling Application Insight on an Extension](devenv-application-insights-for-extensions.md).

- In the tenant on the [!INCLUDE[server](includes/server.md)] service/server.

    For more information, see [Enabling Application Insights](../administration/telemetry-overview.md#enable).

When you create a custom telemetry trace signal, you can specify a telemetry scope. The telemetry scope enables you to send a signal only to the Application Insights resource specified in the extension's app.json. Or to all available resources.

> [!NOTE]
> Having Application Insights resources configured is not required to create custom signals in AL code. 

## Create a custom telemetry trace signal

To create a custom telemetry trace signal, use a LOGMESSAGE method in AL code where you want to trigger the signal. The LOGMESSAGE method defines the information that is sent to Application Insights for a specific operation or activity.

There are two variations of the LOGMESSAGE method. The difference is that one method uses a dictionary object to define custom dimensions for the trace signal. The other method includes two overloads so you don't have to construct a dictionary. You can use these methods in any object, trigger, or method. The methods have the following signatures:  

### Using a dictionary

The LOGMESSAGE method for using a dictionary for dimensions has the following signature:

```al
Session.LogMessage(EventId: String, Message: String, Verbosity: Verbosity, DataClassification: DataClassification, TelemetryScope: TelemetryScope, CustomDimensions: Dictionary of [Text, Text])
```

### Using dimension overloads

The LOGMESSAGE method for using dimension overloads has the following signature:

```al
Session.LogMessage(EventId: String, Message: String, Verbosity: Verbosity, DataClassification: DataClassification, TelemetryScope: TelemetryScope, Dimension1: String, Value1: String [, Dimension2: String] [, Value2: String])
```

### Setting the parameters

Use the parameters to build the dimensions, or columns, that will show for the trace in Application Insights. `Message` and `Verbosity` will appear as general dimensions. All other parameters appear as custom dimensions. 

|Parameter|Description|Dimension|
|---------|-----------|---------------------------------|
|EventID|A text string that assigns an identifier to the telemetry trace signal. The tag can consist of letters, numbers, and special characters. Try to make your tags unique. For example, use at least 8 characters or a prefix, like Cronus-0001 and Cronus-0002.|eventId|
|Message|A text string that specifies the descriptive message for the telemetry trace signal.|message|
|Verbosity<sup>[*](#*)|An enumeration that specifies the severity level of the telemetry trace signal. The value can be `Critical`, `Error`, `Warning`, `Normal`, or `Verbose`. |severityLevel<br /><br />`4`=`Critical`<br />`3`=`Error`<br />`2`=`Warning`<br />`1`=`Normal` <br />`0`=`Verbose`<br />|
|DataClassification[*](#*)|A DataClassification data type that assigns a classification to the telemetry trace signal. For more information, see [Data Classifications](devenv-classifying-data.md#DataClassifications).|dataClassification|
|TelemetryScope|Scope of emitting the telemetry. <ul><li>`extensionpublisher` sends the custom signal only to the Application Insight resource specified in the extension's app.json file</li><li>`all` sends the custom signal to Application Insight resource specified in the extension's app.json file and on the tenant. </li></ul> |telemetryScope
|CustomDimensions|A dictionary of text that defines the custom dimensions for the trace signal in Application Insights. There are several CustomDimensions that will be included in traces by default. See [Default CustomDimensions](#default-customdimensions)|
|Dimension1|A text string that specifies the name of the custom dimension.|
|Value1|A text string that specifies the value of Dimension1.|
|Dimension2|A text string that specifies the name of the custom dimension.|
|Value2|A text string that specifies the value of Dimension2.|

> [!NOTE]
> In Application Insights, the name of custom dimension will be prefixed with `al`. For example, if the dimension string you define in code is `result`, then in the trace logged in Application Insights, the name appears as `alresult`.

### Default CustomDimensions

The following table explains CustomDimensions that are automatically included in ALMessage traces that are sent to Application Insights.

<!--{"telemetrySchemaVersion":"1.2","componentVersion":"20.0.36722.0","environmentType":"Production","aadTenantId":"d88985a1-c863-442c-bb5f-dc622e480a8d","companyName":"CRONUS International Ltd.","component":"Dynamics 365 Business Central Server","eventId":"ALMyExt-0001","clientType":"WebClient","extensionName":"ALlogmessage","alCallerAppName":"Base Application","alObjectId":"50110","alDataClassification":"SystemMetadata","alCallerPublisher":"Microsoft","alresult":"failed","alObjectType":"PageExtension","alCallerAppVersion":"20.0.36796.0","extensionPublisher":"Default publisher","alObjectName":"CustomerListExt","extensionVersion":"1.0.0.0","extensionId":"f2ae006d-deef-4990-828e-4c76906e7171","alreason":"critical error in code"}
 -->
|Dimension|Description or value|
|---------|-----|
|aadTenantId|Specifies the Microsoft Entra tenant ID used for Microsoft Entra authentication. For on-premises, if you aren't using Microsoft Entra authentication, this value is **common**. |
|alCallerAppName|Specifies the name of the extension that emitted the telemetry signal to Application Insights. This is typically the base application.|
|alCallerAppPublishser|Specifies the publisher of the extension that emitted the telemetry signal to Application Insights. This is typically the publisher of the base application, which is `Microsoft`.|
|alCallerAppVersion|Specifies the version number of the extension that emitted the telemetry signal to Application Insights. This is typically the version of the base application.|
|alObjectId|Specifies the ID of the object that called the LOGMESSAGE method.|
|alObjectName|Specifies the name of the object that called the LOGMESSAGE method.|
|alObjectType|Specifies the type of the object that called the LOGMESSAGE method, like `PageExtension` for a page extension object. |
|clientType|Specifies the type of client that ran LOGMESSAGE method, such as **Background** or **Web**. For a list of the client types, see [ClientType Option Type](../developer/methods-auto/clienttype/clienttype-option.md).|
|componentVersion|Specifies the version number of the component that emits telemetry (see the component dimension.)|
|companyName|Specifies the company in Business Central|
|component|**Dynamics 365 Business Central Server**.|
|componentVersion|Specifies the version number of the component that emits telemetry (see the component dimension.)|
|environmentName|Specifies the name of the tenant environment. See [Managing Environments](../administration/tenant-admin-center-environments.md).|
|environmentType|Specifies the environment type for the tenant, such as **Production**, **Sandbox**, **Trial**. See [Environment Types](../administration/tenant-admin-center-environments.md#types-of-environments)|
| extensionName|Specifies the name of the extension that called the LOGMESSAGE method.|
| extensionId|Specifies the ID of the extension that called the LOGMESSAGE method.|
| extensionPublisher|Specifies the publisher of the extension that called the LOGMESSAGE method.|
| extensionVersion|Specifies the version of the compiled extension.|
|deprecatedKeys|A comma-separated list of all the keys that have been deprecated. The keys in this list are still supported but will eventually be removed in the next major release. We recommend that update any queries that use these keys to use the new key name.|
|telemetrySchemaVersion|Specifies the version of the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] telemetry schema.|

## Best practices for designing telemetry event 
When the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] product team designed the partner telemetry feature, we build the following characteristics into it: 
* Telemetry event definitions must treated as an API. Changing custom dimensions is a breaking change (someone might have built reporting or alerting on top of it).
* Telemetry events must be discoverable in docs. If you see someting in telemetry, it should be easy to learn more about it in documentation. We added the custom dimension eventId because of this. It is good practice to keep eventIds unique, also across apps/extensions. 
* Documented: each telemetry event has good documentation, preferably with guidance on how to react on this event.
* Actionable (if possible): before we add a new telemetry event, we ask "what can a customer/partner do with this?" If no good answers come to mind, we do not add the event. 


## Examples

The following code snippets create simple telemetry trace signals. They create a critical-level telemetry signal that is scoped to the signal publisher. For a simple test of this code, add it to the `OnRun` trigger of a codeunit, and then run the codeunit.

**Using a dictionary:**
```AL
trigger OnRun();
var
    CustDimension: Dictionary of [Text, Text];
begin
    CustDimension.Add('result', 'failed');
    CustDimension.Add('reason', 'critical error in code');
    LogMessage('MyExt-0001', 'This is a critical error message', Verbosity::Normal, DATACLASSIFICATION::SystemMetadata, TelemetryScope::ExtensionPublisher, CustDimension);
end;
```

**Using an overload:**

```AL
trigger OnRun();
begin
    LogMessage('MyExt-0001', 'This is a critical error message', Verbosity::Critical, DATACLASSIFICATION::SystemMetadata, TelemetryScope::ExtensionPublisher, 'result', 'failed', 'reason', 'critical error in code');
end;
```

## <a name="*"></a>Design considerations

- For [!INCLUDE[prod_short](../includes/prod_short.md)] on-premises, the **Diagnostic Trace Level** setting on the [!INCLUDE[server](includes/server.md)] instance controls which signals are sent, based on their severity level.

    If the **Diagnostic Trace Level** is set to **Warning** for example, then **Normal** and **Verbose** signals won't be sent to Application Insights. For more information, see [Configuring Business Central Server - General](../administration/configure-server-instance.md#general-settings).

- For privacy reasons, events that have a `DataClassification` other than `SystemMetadata` aren't sent to Application Insight resources set up on the tenant. During development of your extension, it's good practice to have a privacy review of the use of LOGMESSAGE calls to ensure that customer data isn't mistakenly leaked into Application Insights resources. 


<!--
```  
LogMessage('MyExt-0001', 'This is a critical message', Verbosity::Critical, DATACLASSIFICATION::CustomerContent, TelemetryScope::ExtensionPublisher, 'result', 'failed', 'reason', 'critical error in code');
LogMessage('MyExt-0002', 'This is an error message', Verbosity::Error, DATACLASSIFICATION::EndUserIdentifiableInformation, TelemetryScope::ExtensionPublisher, 'result', 'failed', 'reason', 'error in code');
LogMessage('MyExt-0003', 'This is an warning message', Verbosity::Warning, DATACLASSIFICATION::AccountData, TelemetryScope::ExtensionPublisher, 'result', 'succeeded', 'reason', 'warning in code');
LogMessage('MyExt-0004', 'This is an informational message', Verbosity::Normal, DATACLASSIFICATION::OrganizationIdentifiableInformation, TelemetryScope::ExtensionPublisher, 'result', 'succeeded');
LogMessage('MyExt-0005', 'This is an verbose message', Verbosity::Verbose, DATACLASSIFICATION::SystemMetadata, TelemetryScope::ExtensionPublisher, 'result', 'succeeded');
``` 
-->

## See Also

[Instrumenting an Application for Telemetry](devenv-instrument-application-for-telemetry.md)  
[LOGMESSAGE method](methods-auto/session/session-logmessage-string-string-verbosity-dataclassification-telemetryscope-dictionary[text,text]-method.md)  
[LOGMESSAGE method](methods-auto/session/session-logmessage-string-string-verbosity-dataclassification-telemetryscope-string-string-string-string-method.md)  
[Monitoring and Analyzing Telemetry](../administration/telemetry-overview.md)  
