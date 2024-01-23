---
title: "Notification.HasData(Text) Method"
description: "Checks if data was passed to a notification instance as specified by a SETDATA method call."
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
# Notification.HasData(Text) Method
> **Version**: _Available or changed with runtime version 1.0._

Checks if data was passed to a notification instance as specified by a SETDATA method call.


## Syntax
```AL
Value :=   Notification.HasData(Name: Text)
```
## Parameters
*Notification*  
&emsp;Type: [Notification](notification-data-type.md)  
An instance of the [Notification](notification-data-type.md) data type.  

*Name*  
&emsp;Type: [Text](../text/text-data-type.md)  
The name of the data item that is specified by the SETDATA method call.  


## Return Value
*Value*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true**, if there is data; otherwise **false**.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[Notification Data Type](notification-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)