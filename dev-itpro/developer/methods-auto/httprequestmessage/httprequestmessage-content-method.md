---
title: "HttpRequestMessage.Content([HttpContent]) Method"
description: "Gets or sets the contents of the HTTP message."
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
# HttpRequestMessage.Content([HttpContent]) Method
> **Version**: _Available or changed with runtime version 1.0._

Gets or sets the contents of the HTTP message.


## Syntax
```AL
[CurrentContent := ]  HttpRequestMessage.Content([SetContent: HttpContent])
```
> [!NOTE]
> This method can be invoked using property access syntax.
## Parameters
*HttpRequestMessage*  
&emsp;Type: [HttpRequestMessage](httprequestmessage-data-type.md)  
An instance of the [HttpRequestMessage](httprequestmessage-data-type.md) data type.  

*[Optional] SetContent*  
&emsp;Type: [HttpContent](../httpcontent/httpcontent-data-type.md)  
The contents of the HTTP message.  


## Return Value
*[Optional] CurrentContent*  
&emsp;Type: [HttpContent](../httpcontent/httpcontent-data-type.md)  
The contents of the HTTP message.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[HttpRequestMessage Data Type](httprequestmessage-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)