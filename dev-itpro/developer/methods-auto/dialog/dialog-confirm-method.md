---
title: "Dialog.Confirm(Text [, Boolean] [, Any,...]) Method"
description: "Creates a dialog box that prompts the user for a yes or no answer."
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
# Dialog.Confirm(Text [, Boolean] [, Any,...]) Method
> **Version**: _Available or changed with runtime version 1.0._

Creates a dialog box that prompts the user for a yes or no answer. The dialog box is centered on the screen.


## Syntax
```AL
Ok :=   Dialog.Confirm(String: Text [, Default: Boolean] [, Value1: Any,...])
```
> [!NOTE]
> This method can be invoked without specifying the data type name.
## Parameters
*String*  
&emsp;Type: [Text](../text/text-data-type.md)  
Specifies the string that is displayed in the dialog box. Use a backslash (\\) to indicate a new line. The string can be a label that is enabled for multilanguage functionality.  

*[Optional] Default*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
Specifies the default button. If you do not specify a default button, then No is used as the default button.  

*[Optional] Value1*  
&emsp;Type: [Any](../any/any-data-type.md)  
  


## Return Value
*Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  

The message window is automatically sized. The height of the window corresponds to the number of lines and the width corresponds to the length of the longest line.  

We recommend that you always end `Confirm` messages with a question mark. For more information about best practices for end-user messages, see [Progress Windows, Message, Error, and Confirm Methods](../../devenv-progress-windows-message-error-and-confirm-methods.md).  

## Example

In the following example, the Dialog.Confirm method prompts the user for a **true** or **false** answer. 

```al
var
    Question: Text;
    Answer: Boolean;
    CustomerNo: Integer;
    Text000: Label 'Exit without saving changes to customer %1?';
    Text001: Label 'You selected %1.';
begin
    CustomerNo := 01121212;  
    Question := Text000;  
    Answer := Dialog.Confirm(Question, true, CustomerNo);  
    Message(Text001, Answer);  
end;
```  

The first dialog box shows:  

**Exit without saving changes to customer 1121212?**  

If you select the default **true** value, then the second dialog box is shown:  

**You selected true.**  


## See Also
[Dialog Data Type](dialog-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)