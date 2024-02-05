---
title: "HttpResponseMessage Data Type"
description: "Represents an HTTP response message including the status code and data."
ms.author: solsen
ms.custom: na
ms.date: 12/01/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# HttpResponseMessage Data Type
> **Version**: _Available or changed with runtime version 1.0._

Represents an HTTP response message including the status code and data.



## Instance methods
The following methods are available on instances of the HttpResponseMessage data type.

|Method name|Description|
|-----------|-----------|
|[Content()](httpresponsemessage-content-method.md)|Gets the contents of the HTTP response.|
|[Headers()](httpresponsemessage-headers-method.md)|Gets the HTTP response's HTTP headers.|
|[HttpStatusCode()](httpresponsemessage-httpstatuscode-method.md)|Gets the status code of the HTTP response.|
|[IsBlockedByEnvironment()](httpresponsemessage-isblockedbyenvironment-method.md)|Gets a value that indicates if the HTTP response is the result of the environment blocking an outgoing HTTP request.|
|[IsSuccessStatusCode()](httpresponsemessage-issuccessstatuscode-method.md)|Gets a value that indicates if the HTTP response was successful.|
|[ReasonPhrase()](httpresponsemessage-reasonphrase-method.md)|Gets the reason phrase which typically is sent by servers together with the status code.|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks
The size of the `HttpResponseMessage` is determined by the `HttpClient AL Function Response Size` setting on the [!INCLUDE[d365fin_long_md](../../includes/d365fin_long_md.md)] server. The default value is `150`. For more information, see [Microsoft Dynamics 365 Business Central Server Configuration](../../../administration/configure-server-instance.md).

> [!NOTE]   
> For performance reasons all HTTP, JSON, TextBuilder, and XML types are reference types, not value types. Reference types holds a pointer to the data elsewhere in memory, whereas value types store its own data.

## See Also
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  