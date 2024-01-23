---
title: "Session.DefaultClientType() Method"
description: "Gets the default client that is configured for the server instance that is used by the current session."
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
# Session.DefaultClientType() Method
> **Version**: _Available or changed with runtime version 1.0._

Gets the default client that is configured for the server instance that is used by the current session.


## Syntax
```AL
ClientType :=   Session.DefaultClientType()
```
> [!NOTE]
> This method can be invoked using property access syntax.
> [!NOTE]
> This method can be invoked without specifying the data type name.


## Return Value
*ClientType*  
&emsp;Type: [ClientType](../clienttype/clienttype-option.md)  
The default client that is configured for the server instance that is used by the current session.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  
 You can use DefaultClientType in a GetURL Method call to get the URL of the default client.  

## Example 1

 In the following example, DefaultClientType is used to return the default client type that is configured for the [!INCLUDE[d365fin_server_md](../../includes/d365fin_server_md.md)] instance that is used by the current session.  

```al
if DefaultClientType = ClientType::Web then  
  Message('The default client is Web client');  
```  

## Example 2

 In the following example, DefaultClientType is used as a parameter in the GetURL method to return the URL of the default client that is configured for the [!INCLUDE[d365fin_server_md](../../includes/d365fin_server_md.md)] instance.  

```al
url := GetURL(DefaultClientType);  
Message('The URL is %1.', url);  
```  

## See Also
[Session Data Type](session-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)