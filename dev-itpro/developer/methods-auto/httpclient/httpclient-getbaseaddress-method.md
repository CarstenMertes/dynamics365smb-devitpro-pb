---
title: "HttpClient.GetBaseAddress() Method"
description: "Gets the base address of Uniform Resource Identifier (URI) of the Internet resource used when sending requests."
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
# HttpClient.GetBaseAddress() Method
> **Version**: _Available or changed with runtime version 1.0._

Gets the base address of Uniform Resource Identifier (URI) of the Internet resource used when sending requests.


## Syntax
```AL
CurrentBaseAddress :=   HttpClient.GetBaseAddress()
```
> [!NOTE]
> This method can be invoked using property access syntax.
## Parameters
*HttpClient*  
&emsp;Type: [HttpClient](httpclient-data-type.md)  
An instance of the [HttpClient](httpclient-data-type.md) data type.  

## Return Value
*CurrentBaseAddress*  
&emsp;Type: [Text](../text/text-data-type.md)  
The base address of URI of the Internet resource used when sending requests.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[HttpClient Data Type](httpclient-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)