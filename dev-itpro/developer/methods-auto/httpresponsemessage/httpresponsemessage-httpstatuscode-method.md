---
title: "HttpResponseMessage.HttpStatusCode() Method"
description: "Gets the status code of the HTTP response."
ms.author: solsen
ms.custom: na
ms.date: 07/07/2021
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# HttpResponseMessage.HttpStatusCode() Method
> **Version**: _Available or changed with runtime version 1.0._

Gets the status code of the HTTP response.


## Syntax
```AL
StatusCode :=   HttpResponseMessage.HttpStatusCode()
```
> [!NOTE]
> This method can be invoked using property access syntax.

## Parameters
*HttpResponseMessage*  
&emsp;Type: [HttpResponseMessage](httpresponsemessage-data-type.md)  
An instance of the [HttpResponseMessage](httpresponsemessage-data-type.md) data type.  

## Return Value
*StatusCode*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The status code of the HTTP response.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## HTTP status codes

[!INCLUDE[httpStatusCodes](../../../includes/include-http-status-codes.md)]


## See Also
[HttpResponseMessage Data Type](httpresponsemessage-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)