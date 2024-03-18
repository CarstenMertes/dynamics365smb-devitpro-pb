---
title: "NavApp.GetModuleInfo(Guid, var ModuleInfo) Method"
description: "Gets information about the specified AL application."
ms.author: solsen
ms.custom: na
ms.date: 02/02/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# NavApp.GetModuleInfo(Guid, var ModuleInfo) Method
> **Version**: _Available or changed with runtime version 1.0._

Gets information about the specified AL application.


## Syntax
```AL
[Ok := ]  NavApp.GetModuleInfo(AppId: Guid, var Info: ModuleInfo)
```
## Parameters
*AppId*  
&emsp;Type: [Guid](../guid/guid-data-type.md)  
The ID of the application for which to retrieve information.  

*Info*  
&emsp;Type: [ModuleInfo](../moduleinfo/moduleinfo-data-type.md)  
A value containing information about the application with the given ID.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the information could be retrieved, otherwise **false**. If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[NavApp Data Type](navapp-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)