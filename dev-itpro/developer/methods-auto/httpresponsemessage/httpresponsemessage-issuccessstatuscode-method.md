---
title: "HttpResponseMessage.IsSuccessStatusCode() Method"
description: "Gets a value that indicates if the HTTP response was successful."
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
# HttpResponseMessage.IsSuccessStatusCode() Method
> **Version**: _Available or changed with runtime version 1.0._

Gets a value that indicates if the HTTP response was successful.


## Syntax
```AL
IsSuccessStatusCode :=   HttpResponseMessage.IsSuccessStatusCode()
```
> [!NOTE]
> This method can be invoked using property access syntax.

## Parameters
*HttpResponseMessage*  
&emsp;Type: [HttpResponseMessage](httpresponsemessage-data-type.md)  
An instance of the [HttpResponseMessage](httpresponsemessage-data-type.md) data type.  

## Return Value
*IsSuccessStatusCode*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
A value that indicates if the HTTP response was successful. **true** if StatusCode was in the range 200-299; otherwise **false**.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[HttpResponseMessage Data Type](httpresponsemessage-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)