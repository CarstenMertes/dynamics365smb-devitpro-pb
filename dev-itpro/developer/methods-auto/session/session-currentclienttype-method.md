---
title: "Session.CurrentClientType() Method"
description: "Gets the client type that is running in current session."
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
# Session.CurrentClientType() Method
> **Version**: _Available or changed with runtime version 1.0._

Gets the client type that is running in current session.


## Syntax
```AL
ClientType :=   Session.CurrentClientType()
```
> [!NOTE]
> This method can be invoked using property access syntax.
> [!NOTE]
> This method can be invoked without specifying the data type name.


## Return Value
*ClientType*  
&emsp;Type: [ClientType](../clienttype/clienttype-option.md)  
The client type that is running in current session.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  
You can use CurrentClientType as a parameter in the [GetURL Method](../system/system-geturl-clienttype-string-objecttype-integer-table-boolean-method.md) to get the URL of the current client.  

## Example 1

In the following example, CurrentClientType is used to get the client type for the session and return a message if the session uses the [!INCLUDE[d365fin_tablet_md](../../includes/d365fin_tablet_md.md)].  

```al
if CurrentClientType = ClientType::Tablet then  
  Message('The session is running the Tablet client');  
```  

## Example 2

 In the following example, CurrentClientType is used as a parameter of the [GetURL Method](../system/system-geturl-clienttype-string-objecttype-integer-table-boolean-method.md) to return the URL of the client that invokes the code.  

```al
url := GetURL(CurrentClientType);  
Message('The URL is %1.', url);  
```  


## See Also
[Session Data Type](session-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)