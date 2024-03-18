---
title: "IsolatedStorage.Contains(Text [, DataScope]) Method"
description: "Determines whether the storage contains a value with the specified key."
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
# IsolatedStorage.Contains(Text [, DataScope]) Method
> **Version**: _Available or changed with runtime version 2.0._

Determines whether the storage contains a value with the specified key.


## Syntax
```AL
HasValue :=   IsolatedStorage.Contains(Key: Text [, DataScope: DataScope])
```
## Parameters
*Key*  
&emsp;Type: [Text](../text/text-data-type.md)  
The key to locate in the storage.  

*[Optional] DataScope*  
&emsp;Type: [DataScope](../datascope/datascope-option.md)  
The scope in which to check for the existence of a value with the given key. If a value is not passed in, the default value DataScope::Module will be used.  


## Return Value
*HasValue*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if a value with the specified key exists in the storage, otherwise **false**.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[IsolatedStorage Data Type](isolatedstorage-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)