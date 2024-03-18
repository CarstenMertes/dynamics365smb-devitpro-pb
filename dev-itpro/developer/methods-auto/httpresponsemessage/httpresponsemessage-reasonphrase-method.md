---
title: "HttpResponseMessage.ReasonPhrase() Method"
description: "Gets the reason phrase which typically is sent by servers together with the status code."
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
# HttpResponseMessage.ReasonPhrase() Method
> **Version**: _Available or changed with runtime version 1.0._

Gets the reason phrase which typically is sent by servers together with the status code.


## Syntax
```AL
ReasonPhrase :=   HttpResponseMessage.ReasonPhrase()
```
> [!NOTE]
> This method can be invoked using property access syntax.
## Parameters
*HttpResponseMessage*  
&emsp;Type: [HttpResponseMessage](httpresponsemessage-data-type.md)  
An instance of the [HttpResponseMessage](httpresponsemessage-data-type.md) data type.  

## Return Value
*ReasonPhrase*  
&emsp;Type: [Text](../text/text-data-type.md)  
The reason phrase sent by the server.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[HttpResponseMessage Data Type](httpresponsemessage-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)