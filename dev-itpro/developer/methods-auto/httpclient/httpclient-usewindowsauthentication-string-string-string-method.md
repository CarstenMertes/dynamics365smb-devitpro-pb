---
title: "HttpClient.UseWindowsAuthentication(Text, Text [, Text]) Method"
description: "Sets the HttpClient credentials to use the specified network credentials for Windows authentication."
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
# HttpClient.UseWindowsAuthentication(Text, Text [, Text]) Method
> **Version**: _Available or changed with runtime version 3.0._

Sets the HttpClient credentials to use the specified network credentials for Windows authentication. If this method is invoked after any HTTP request has started; a runtime error occurs.

> [!NOTE]
> This method is supported only in Business Central on-premises.

## Syntax
```AL
[Result := ]  HttpClient.UseWindowsAuthentication(UserName: Text, Password: Text [, Domain: Text])
```
## Parameters
*HttpClient*  
&emsp;Type: [HttpClient](httpclient-data-type.md)  
An instance of the [HttpClient](httpclient-data-type.md) data type.  

*UserName*  
&emsp;Type: [Text](../text/text-data-type.md)  
The Windows user name.  

*Password*  
&emsp;Type: [Text](../text/text-data-type.md)  
The password.  

*[Optional] Domain*  
&emsp;Type: [Text](../text/text-data-type.md)  
The user's domain.  


## Return Value
*[Optional] Result*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the operation was successful; otherwise **false**.   If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[HttpClient Data Type](httpclient-data-type.md)  
[Getting Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)