---
title: "HttpContent.ReadAs(var SecretText) Method"
description: "Reads the content into the provided secure text."
ms.author: solsen
ms.custom: na
ms.date: 09/06/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# HttpContent.ReadAs(var SecretText) Method
> **Version**: _Available or changed with runtime version 12.0._

Reads the content into the provided secure text.


## Syntax
```AL
[Ok := ]  HttpContent.ReadAs(var OutputSecretText: SecretText)
```
## Parameters
*HttpContent*  
&emsp;Type: [HttpContent](httpcontent-data-type.md)  
An instance of the [HttpContent](httpcontent-data-type.md) data type.  

*OutputSecretText*  
&emsp;Type: [SecretText](../secrettext/secrettext-data-type.md)  
The variable that will contain the HTTP content as a secret text.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
Accessing the HttpContent property of HttpResponseMessage in a case when the request fails will result in an error. If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[HttpContent Data Type](httpcontent-data-type.md)  
[Getting Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)