---
title: "Option Data Type"
description: "Denotes an option value."
ms.author: solsen
ms.custom: na
ms.date: 06/23/2021
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Option Data Type
> **Version**: _Available or changed with runtime version 1.0._

Denotes an option value. In the code snippet below, you can see how the Option data type is declared.




[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Syntax example

```al
procedure HelloWithOptions(OptionParameter : Option Alpha, "Bra-vo")
    var 
        OptionVariable : Option C, "or D";
    begin
        Message('%1',OptionParameter::Alpha);
        Message('%1',OptionVariable::C);
    end;
```


> [!NOTE]  
> It is not possible to reference the members of the `OptionParameter` from outside the body of the procedure. 
  
## Remarks

In the [OptionString Property](../../properties/devenv-optionmembers-field-property.md) of the field or variable, you can enter the option values as a comma-separated list. The Option type is a zero-based enumerator type, which means that the option values are assigned to sequential numbers, starting with 0. You can convert option data types to integers.  
 <!-- 
 For more information about option variables in multilanguage-enabled applications, see [Developing Multilanguage-Enabled Applications](../../dynamics-nav/Developing-Multilanguage-Enabled-Applications.md).  
 --> 

## Example 1

The following code sample shows how to define an option field in a table.  
  
```al
field(0; PreferredContactMethodCode; Option)
{
    Caption = 'Preferred Method of Contact';
    // The OptionMembers property must be defined on an option field. It specifies which values can the field take.
    OptionMembers = Any,Email,Phone,Fax,Mail;
}
```

## Example 2

This example shows how you can use the value of an option field as a constant in your AL code.  
  
```al
PurchHeaderRec."Document Type" := PurchHeaderRec."Document Type"::Invoice;   
```

## See Also

[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)