---
title: "OnBeforeValidate Trigger"
description: "OnBeforeValidate trigger in AL for Business Central."
ms.custom: na
ms.date: 04/01/2021
ms.reviewer: solsen
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: reference
ms.author: t-blrobl
author: blrobl
---

# OnBeforeValidate Trigger

Runs before the user input is validated. 

## Applies to  

- Fields  
  
## Remarks  

This trigger is run before the default validation behavior is executed on a record field entry, which are default checks such as data type validation. An error message displays if an error occurs in the trigger code. In case of an error, the user entry is not written to the database.  

It applies to an already existing table field when it is being modified in a table extension. 

## Example

```AL
tableextension 50111 "CustomerExt" extends Customer
{
    fields
    {
        modify("Address 2")
        {
            trigger OnBeforeValidate()
            begin
                if (rec.Address = '') then
                    error('Please, input a first address before specifying a second one.');
            end;
        }
    }
}
```

## See Also  

[Triggers](devenv-triggers.md)  
[Table and Field Triggers](devenv-table-and-field-triggers.md)  
[OnAfterValidate Trigger](devenv-onaftervalidate-fields-trigger.md)  
[Table Properties](../properties/devenv-table-properties.md)    
