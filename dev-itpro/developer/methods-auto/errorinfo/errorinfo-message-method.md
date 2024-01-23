---
title: "ErrorInfo.Message([Text]) Method"
description: "Specifies the message that will be sent to telemetry."
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
# ErrorInfo.Message([Text]) Method
> **Version**: _Available or changed with runtime version 3.0._

Specifies the message that will be sent to telemetry. For a 'Client' error type, the message will also be appear in the client.


## Syntax
```AL
[Message := ]  ErrorInfo.Message([Message: Text])
```
> [!NOTE]
> This method can be invoked using property access syntax.
## Parameters
*ErrorInfo*  
&emsp;Type: [ErrorInfo](errorinfo-data-type.md)  
An instance of the [ErrorInfo](errorinfo-data-type.md) data type.  

*[Optional] Message*  
&emsp;Type: [Text](../text/text-data-type.md)  
The message of the ErrorInfo  


## Return Value
*[Optional] Message*  
&emsp;Type: [Text](../text/text-data-type.md)  
The current message of the ErrorInfo.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

Set the **Message** property on error dialogs that are presented to the user. For advice on how to use the title to describe what’s wrong and enable the user to quickly scan the meaning of the error, see [User experience guidelines for errors](../../devenv-error-handling-guidelines.md#error-message-body).  

Setting the Message property on error dialogs is required. For more information on how to express error messages, see [Error message best practices - what to say?](../../devenv-error-handling-guidelines.md#error_message_best_practices).


## Example 

```AL
var 
    dimension: Text[30];
    vendorCode: Text[30];
    MyErrorInfo: ErrorInfo;
begin
    // set up the error info object
    MyErrorInfo.Message(
        StrSubstNo('The dimension value must be blank for the dimension %1 for Vendor %2', dimension, vendorCode)
    );
    MyErrorInfo.DetailedMessage('Add some text to help the person troubleshooting this error.');
    // maybe set more properties

    Error(MyErrorInfo);
end
```


## See Also

[ErrorInfo Data Type](errorinfo-data-type.md)  
[User experience guidelines for errors](../../devenv-error-handling-guidelines.md)  
[AL error handling](../../devenv-al-error-handling.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)