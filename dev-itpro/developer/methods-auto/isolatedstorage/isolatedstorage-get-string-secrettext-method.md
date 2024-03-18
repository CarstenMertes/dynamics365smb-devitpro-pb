---
title: "IsolatedStorage.Get(Text, var SecretText) Method"
description: "Gets the value associated with the specified key."
ms.author: solsen
ms.custom: na
ms.date: 02/26/2024
ms.tgt_pltfrm: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# IsolatedStorage.Get(Text, var SecretText) Method
> **Version**: _Available or changed with runtime version 13.0._

Gets the value associated with the specified key.


## Syntax
```AL
[Ok := ]  IsolatedStorage.Get(Key: Text, var Value: SecretText)
```
## Parameters
*Key*  
&emsp;Type: [Text](../text/text-data-type.md)  
The key of the value to get. If the specified key is not found an error will be reported.  

*Value*  
&emsp;Type: [SecretText](../secrettext/secrettext-data-type.md)  
The value that is associated with the specified key.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the value was retrieved successfully, otherwise **false**. If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[IsolatedStorage Data Type](isolatedstorage-data-type.md)  
[Getting Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)