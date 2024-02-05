---
title: "ErrorInfo.AddAction(Text, Integer, Text, Text) Method"
description: "Specifies an action for the error."
ms.author: solsen
ms.custom: na
ms.date: 01/03/2024
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# ErrorInfo.AddAction(Text, Integer, Text, Text) Method
> **Version**: _Available or changed with runtime version 12.0._

Specifies an action for the error.


## Syntax
```AL
 ErrorInfo.AddAction(Caption: Text, CodeunitID: Integer, MethodName: Text, Description: Text)
```
## Parameters
*ErrorInfo*  
&emsp;Type: [ErrorInfo](errorinfo-data-type.md)  
An instance of the [ErrorInfo](errorinfo-data-type.md) data type.  

*Caption*  
&emsp;Type: [Text](../text/text-data-type.md)  
The text string that appears as the caption of the action in the error UI. The string can be a label that is enabled for multilanguage functionality.  

*CodeunitID*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The ID of the codeunit to run when the action is initiated from the error UI. The codeunit should contain at least one global method to be called by the error action. The global method must have an ErrorInfo data type parameter for accepting the ErrorInfo object.  

*MethodName*  
&emsp;Type: [Text](../text/text-data-type.md)  
The name of the method in the codeunit, which is specified by the CodeunitID parameter, that you want to run for the action.  

*Description*  
&emsp;Type: [Text](../text/text-data-type.md)  
The text that appears as the tooltip of the action in the error UI.  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

The semantics of this method is the same as the version without a Description parameter. For more information, see [AddAction(Text, Integer, Text)](errorinfo-addaction-string-integer-string-method.md).

## See Also

[ErrorInfo Data Type](errorinfo-data-type.md)  
[Actionable errors](../../devenv-actionable-errors.md)  
[Error handling](../../devenv-al-error-handling.md)   
[Getting Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)