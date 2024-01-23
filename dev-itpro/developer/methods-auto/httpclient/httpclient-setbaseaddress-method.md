---
title: "HttpClient.SetBaseAddress(Text) Method"
description: "Sets the base address of Uniform Resource Identifier (URI) of the Internet resource used when sending requests."
ms.author: solsen
ms.custom: na
ms.date: 03/24/2022
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# HttpClient.SetBaseAddress(Text) Method
> **Version**: _Available or changed with runtime version 1.0._

Sets the base address of Uniform Resource Identifier (URI) of the Internet resource used when sending requests.


## Syntax
```AL
[Ok := ]  HttpClient.SetBaseAddress(NewBaseAddress: Text)
```
## Parameters
*HttpClient*  
&emsp;Type: [HttpClient](httpclient-data-type.md)  
An instance of the [HttpClient](httpclient-data-type.md) data type.  

*NewBaseAddress*  
&emsp;Type: [Text](../text/text-data-type.md)  
The base address of the Uniform Resource Identifier (URI) of the Internet resource used when sending requests.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the operation was successful; otherwise **false**.   If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[HttpClient Data Type](httpclient-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)