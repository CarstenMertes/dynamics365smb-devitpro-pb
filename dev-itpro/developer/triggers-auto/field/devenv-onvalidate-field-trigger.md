---
title: "OnValidate (Field) Trigger"
description: "Runs when user input is validated."
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

# OnValidate (Field) Trigger
> **Version**: _Available or changed with runtime version 1.0._

Runs when user input is validated.


## Syntax
```AL
trigger OnValidate()
begin
    ...
end;
```



[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  

This trigger is run after the default validation behavior when data is entered in a field. During the default validation behavior, the system checks that the data type of the value entered matches the one defined for the field and that it complies with the property constraints set up in such field before the validation occurs. An error message displays if an error occurs in the trigger code. In case of an error, the user entry is not written to the database.  

The **OnValidate** trigger is also a field trigger at the page level. For more information, see [OnValidate (Page Fields) Trigger](../pagefield/devenv-onvalidate-pagefield-trigger.md). If both the table field and page field triggers are defined, then the **OnValidate** trigger on the table field is run before the **OnValidate** trigger on the page field.  

## Example

```AL
tableextension 50111 "CustomerExt" extends Customer
{
    fields
    {
        field(50112; Acronym; Text[15])
        {
            trigger OnValidate()
            begin
                rec.Acronym := rec.Acronym.ToUpper();
            end;
        }
    }
}
```

## See Also  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  
[OnValidate (Page Field) Trigger](../pagefield/devenv-onvalidate-pagefield-trigger.md)
