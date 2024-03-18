---
title: "IsolatedStorage.Delete(Text [, DataScope]) Method"
description: "Deletes the value with the specified key from the isolated storage."
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
# IsolatedStorage.Delete(Text [, DataScope]) Method
> **Version**: _Available or changed with runtime version 2.0._

Deletes the value with the specified key from the isolated storage.


## Syntax
```AL
[Ok := ]  IsolatedStorage.Delete(Key: Text [, DataScope: DataScope])
```
## Parameters
*Key*  
&emsp;Type: [Text](../text/text-data-type.md)  
The key of the value to remove.  

*[Optional] DataScope*  
&emsp;Type: [DataScope](../datascope/datascope-option.md)  
The scope from which to remove the value with the given key. If a value is not passed in, the default value DataScope::Module will be used.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the value with the given key was successfully deleted from isolated storage, otherwise **false**. If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[IsolatedStorage Data Type](isolatedstorage-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)