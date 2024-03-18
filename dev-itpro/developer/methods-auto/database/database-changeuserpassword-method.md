---
title: "Database.ChangeUserPassword(Text, Text) Method"
description: "Changes the password for the current user."
ms.author: solsen
ms.custom: na
ms.date: 03/02/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Database.ChangeUserPassword(Text, Text) Method
> **Version**: _Available or changed with runtime version 1.0._

Changes the password for the current user.

> [!NOTE]
> This method is supported only in Business Central on-premises.

## Syntax
```AL
[Ok := ]  Database.ChangeUserPassword(OldPassword: Text, NewPassword: Text)
```
> [!NOTE]
> This method can be invoked without specifying the data type name.
## Parameters
*OldPassword*  
&emsp;Type: [Text](../text/text-data-type.md)  
The old password for the user.  

*NewPassword*  
&emsp;Type: [Text](../text/text-data-type.md)  
The new password for the user.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the operation was successful; otherwise **false**.   If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[Database Data Type](database-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)