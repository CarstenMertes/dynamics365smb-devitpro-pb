---
title: "HttpContent.GetHeaders(var HttpHeaders) Method"
description: "Gets the HTTP content headers as defined in RFC 2616."
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
# HttpContent.GetHeaders(var HttpHeaders) Method
> **Version**: _Available or changed with runtime version 1.0._

Gets the HTTP content headers as defined in RFC 2616.


## Syntax
```AL
[Ok := ]  HttpContent.GetHeaders(var Headers: HttpHeaders)
```
## Parameters
*HttpContent*  
&emsp;Type: [HttpContent](httpcontent-data-type.md)  
An instance of the [HttpContent](httpcontent-data-type.md) data type.  

*Headers*  
&emsp;Type: [HttpHeaders](../httpheaders/httpheaders-data-type.md)  
The HTTP headers associated with the content.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
Accessing the HttpContent property of HttpResponseMessage in a case when the request fails will result in an error. If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[HttpContent Data Type](httpcontent-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)