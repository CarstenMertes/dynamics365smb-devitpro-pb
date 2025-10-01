---
title: "TelemetryScope system option"
description: "Represents the emission scope of the telemetry signal."
ms.author: solsen
ms.date: 08/08/2025
ms.topic: reference
author: SusanneWindfeldPedersen
ms.reviewer: solsen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# TelemetryScope option type
> **Version**: _Available or changed with runtime version 5.4._

Represents the emission scope of the telemetry signal.

## Members
|  Member  |  Description  |
|----------------|---------------|
|ExtensionPublisher|Emit telemetry to extensions publisher's account.|
|All|Emit telemetry to extension publisher's and partner's telemetry account .|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Examples

```al
if not FileManagement.ServerFileExists(ServerFile) then begin
            LogInternalError(SomethingWentWrongErr, DataClassification::SystemMetadata, Verbosity::Error);
```

```al
if not XmlDocument.ReadFrom('<?xml version="1.0" encoding="UTF-8"?>' + '<Elster xmlns="' + XmlNameSpace + '"></Elster>', XmlSubDoc) then
            LogInternalError(XMLDocHasNotBeenCreatedErr, DataClassification::SystemMetadata, Verbosity::Error);
```

## Related information  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  