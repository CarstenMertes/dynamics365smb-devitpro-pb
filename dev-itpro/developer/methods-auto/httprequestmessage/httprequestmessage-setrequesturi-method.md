---
title: "HttpRequestMessage.SetRequestUri(Text) Method"
description: "Sets the URI used for the HTTP request."
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
# HttpRequestMessage.SetRequestUri(Text) Method
> **Version**: _Available or changed with runtime version 1.0._

Sets the URI used for the HTTP request.


## Syntax
```AL
[Ok := ]  HttpRequestMessage.SetRequestUri(RequestUri: Text)
```
## Parameters
*HttpRequestMessage*  
&emsp;Type: [HttpRequestMessage](httprequestmessage-data-type.md)  
An instance of the [HttpRequestMessage](httprequestmessage-data-type.md) data type.  

*RequestUri*  
&emsp;Type: [Text](../text/text-data-type.md)  
The URI to use for the HTTP request.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the URI was set successfully, otherwise **false**. If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[HttpRequestMessage Data Type](httprequestmessage-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)