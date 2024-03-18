---
title: "HttpClient.DefaultRequestHeaders() Method"
description: "Gets the default request headers which should be sent with each request."
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
# HttpClient.DefaultRequestHeaders() Method
> **Version**: _Available or changed with runtime version 1.0._

Gets the default request headers which should be sent with each request.


## Syntax
```AL
CurrentDefaultRequestHeaders :=   HttpClient.DefaultRequestHeaders()
```
> [!NOTE]
> This method can be invoked using property access syntax.

## Parameters
*HttpClient*  
&emsp;Type: [HttpClient](httpclient-data-type.md)  
An instance of the [HttpClient](httpclient-data-type.md) data type.  

## Return Value
*CurrentDefaultRequestHeaders*  
&emsp;Type: [HttpHeaders](../httpheaders/httpheaders-data-type.md)  
The default request headers which should be sent with each request.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks
The [HttpHeaders](../httpheaders/httpheaders-data-type.md) variable is a reference type. When you add a header to this variable, the default headers are changed. You cannot set another HttpHeaders object as a default header, you have to update the header fetched from [HttpClient](httpclient-data-type.md).


## See Also
[HttpClient Data Type](httpclient-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)