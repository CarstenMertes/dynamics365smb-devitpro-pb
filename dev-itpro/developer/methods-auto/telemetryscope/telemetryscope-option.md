---
title: "TelemetryScope System Option"
description: "Represents the emission scope of the telemetry signal."
ms.author: solsen
ms.custom: na
ms.date: 05/11/2021
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# TelemetryScope Option Type
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

## See Also  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  