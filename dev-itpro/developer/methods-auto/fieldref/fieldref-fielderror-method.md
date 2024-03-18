---
title: "FieldRef.FieldError([String]) Method"
description: "Stops the execution of the code, causing a run-time error, and creates an error message for a field."
ms.author: solsen
ms.custom: na
ms.date: 07/07/2021
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# FieldRef.FieldError([String]) Method
> **Version**: _Available or changed with runtime version 1.0._

Stops the execution of the code, causing a run-time error, and creates an error message for a field.


## Syntax
```AL
 FieldRef.FieldError([Text: String])
```
## Parameters
*FieldRef*  
&emsp;Type: [FieldRef](fieldref-data-type.md)  
An instance of the [FieldRef](fieldref-data-type.md) data type.  

*[Optional] Text*  
&emsp;Type: [String](/dynamics365/business-central/dev-itpro/developer/methods-auto/text/text-data-type)  
Use this optional parameter to include the text of the error message. If this parameter is not present, default text will be used.  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)


## Remarks

Similar to a run-time error, this method causes any transaction to be ended automatically.  
  
This method is like the FieldError Method for the Record data type. For examples, see [FieldError Method \(Record\)](../../methods-auto/record/record-fielderror-method.md).  
  
## Example

The following example opens table 18 \(Customer\) as a RecordRef variable that is named CustomerRecref. The CustomerName variable is initialized with a blank text. `CustomerRecref.Field` creates a FieldRef that is named MyFieldRef for field1 \(No.\) and selects record 30000. Field 2 \(Name\) is then selected for record 30000. If the CustomerName variable is a blank text, then `MyFieldRef.FieldError` is executed and an error message is displayed. The text in Text000 text constant is inserted into the error message that is displayed by [!INCLUDE[d365fin_md](../../includes/d365fin_md.md)]. 

```al
var
    MyFieldRef: FieldRef;
    CustomerRecref: RecordRef;
    CustomerName: Text;
    Text000: Label 'cannot be blank';
begin
    CustomerRecref.Open(18);  
    CustomerName := '';  
    MyFieldRef := CustomerRecref.Field(1);  
    MyFieldRef.Value('30000');  
    MyFieldRef := CustomerRecref.Field(2);  
    if CustomerName = '' then  
      MyFieldRef.FieldError(Text000)  
    else  
      //Do some processing  
end;
```  
  
This code example displays the following error message:  
  
**Name cannot be blank in Customer No.="30000".**  
  
## Programming Guidelines

We recommend the following guidelines for error messages:  
  
- Describe what is wrong and how to solve the problem.  
- Write a short descriptive message. Do not use more words than necessary.  
- Note that a period is automatically inserted at the end of a FieldError.  
- Use a text constant for the *Text* parameter.  
  
For more information, see [Progress Windows, Message, Error, and Confirm Methods](../../devenv-progress-windows-message-error-and-confirm-methods.md). 

 
## See Also
[FieldRef Data Type](fieldref-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)