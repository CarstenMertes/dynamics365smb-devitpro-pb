---
title: "File.IsPathTemporary(Text) Method"
description: "Validates whether the given path is located in the current users temporary folder within the current service."
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
# File.IsPathTemporary(Text) Method
> **Version**: _Available or changed with runtime version 2.0._

Validates whether the given path is located in the current users temporary folder within the current service.

> [!NOTE]
> This method is supported only in Business Central on-premises.

## Syntax
```AL
[Ok := ]  File.IsPathTemporary(Name: Text)
```
> [!NOTE]
> This method can be invoked without specifying the data type name.
## Parameters
*Name*  
&emsp;Type: [Text](../text/text-data-type.md)  
The name of the file, including the path.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the name point to a location is the users temporary folder within the current service; **false** otherwise. If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[File Data Type](file-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)