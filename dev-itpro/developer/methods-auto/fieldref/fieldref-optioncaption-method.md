---
title: "FieldRef.OptionCaption() Method"
description: "Gets the option caption of the field that is currently selected."
ms.author: solsen
ms.custom: na
ms.date: 03/24/2022
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# FieldRef.OptionCaption() Method
> **Version**: _Available or changed with runtime version 1.0._

Gets the option caption of the field that is currently selected.


## Syntax
```AL
OptionCaption :=   FieldRef.OptionCaption()
```
> [!NOTE]
> This method can be invoked using property access syntax.
## Parameters
*FieldRef*  
&emsp;Type: [FieldRef](fieldref-data-type.md)  
An instance of the [FieldRef](fieldref-data-type.md) data type.  

## Return Value
*OptionCaption*  
&emsp;Type: [Text](../text/text-data-type.md)  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

The option caption of the field is returned as a comma-separated string.  
  
If the field is not an Option, an empty string is returned.  
  
This method returns an error if no field is selected.  
  
## Example

The following example opens the Item table as a RecordRef variable that is named ItemRecref. and creates a reference to field 19 \(Price/Profit Calculation field\), which is an Option field. The OptionCaption method retrieves the caption of the option field and displays the options as a comma-separated list. 

```al
var
    MyFieldRef: FieldRef;
    ItemRecref: RecordRef;
    OptionCaption: Text;
begin
    ItemRecref.Open(Database::Item);  
    MyFieldRef := ItemRecref.Field(19);  
    OptionCaption := MyFieldRef.OptionCaption;  
    Message('%1', OptionCaption);  
end;
```  
  
## See Also

[FieldRef Data Type](fieldref-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)