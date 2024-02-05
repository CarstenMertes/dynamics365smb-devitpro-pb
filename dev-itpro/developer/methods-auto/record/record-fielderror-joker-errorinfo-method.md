---
title: "Record.FieldError(Any, ErrorInfo) Method"
description: "Stops the execution of the code causing a run-time error, and creates an error message for a field."
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
# Record.FieldError(Any, ErrorInfo) Method
> **Version**: _Available or changed with runtime version 8.1._

Stops the execution of the code causing a run-time error, and creates an error message for a field.


## Syntax
```AL
 Record.FieldError(Field: Any, ErrorInfo: ErrorInfo)
```
## Parameters
*Record*  
&emsp;Type: [Record](record-data-type.md)  
An instance of the [Record](record-data-type.md) data type.  

*Field*  
&emsp;Type: [Any](../any/any-data-type.md)  
The field for which you want to create an error message.  

*ErrorInfo*  
&emsp;Type: [ErrorInfo](../errorinfo/errorinfo-data-type.md)  
Additional information to include in the error if the test fails.  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  

Like a runtime error, this method causes the system to automatically end any transaction.  
  
## Programming guidelines

The following guidelines for error messages are recommended:  
  
- Describe what is wrong and how to solve the problem.  
- Write a short descriptive message. Do not use more words than necessary.  
- Note that a period is automatically inserted at the end of a FieldError.  
- Use a label data type for the *Text* parameter.  
  
For more information, see [Progress Windows, Message, Error, and Confirm Methods](../../devenv-progress-windows-message-error-and-confirm-methods.md).
  
### Example 1
 
In the first example, there is no *Text* parameter and the field does not have a value.
  
```al
var
    CustomerRec: Record Customer;

...
CustomerRec."No." := '';  
CustomerRec.FieldError("No.");  

```  
  
The following message is displayed:  
  
**You must specify No. in Customer No.=''.**  
  
### Example 2
 
In the next example, there is no *Text* parameter and the field has a value.
  
```al
var
    CustomerRec: Record Customer;

...  
CustomerRec."No." := 'NEW 3500';  
CustomerRec.FieldError("No.");  
```  
  
The following message is displayed:  
  
**No. must not be NEW 3500 in Customer No.='NEW 3500'.**  
  
### Example 3

The third example uses a non-empty string as the *Text* parameter.
  
```al
var
    CustomerRec: Record Customer;
    Text001: Label 'is not valid';

...
CustomerRec."No." := 'NEW 3500';  
CustomerRec.FieldError("No.", Text001);  
```  
  
The following message is displayed:  
  
**No. is not valid in Customer No.='NEW 3500'.**  

## See Also

[Record Data Type](record-data-type.md)
[Get Started with AL](../../devenv-get-started.md)    
[Developing Extensions](../../devenv-dev-overview.md)  