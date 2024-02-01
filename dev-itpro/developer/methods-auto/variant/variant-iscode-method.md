---
title: "Variant.IsCode() Method"
description: "Indicates whether an AL variant contains a Code variable."
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
# Variant.IsCode() Method
> **Version**: _Available or changed with runtime version 1.0._

Indicates whether an AL variant contains a Code variable.


## Syntax
```AL
Ok :=   Variant.IsCode()
```
> [!NOTE]
> This method can be invoked using property access syntax.

## Parameters
*Variant*  
&emsp;Type: [Variant](variant-data-type.md)  
An instance of the [Variant](variant-data-type.md) data type.  

## Return Value
*Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the AL variant contains a Code variable, otherwise **false**.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Example  
 The following example determines whether an AL variant contains a code variable. The code initializes the MyCode variable with a string value. The MyCode variable is assigned to the variant variable that is named MyVariant. The **IsCode** method determines whether the variant contains a code variable and stores the return value in the varResult variable. In this case, the variant contains a code variable so **true** is returned and displayed in a message box. The [IsText Method (Variant)](variant-istext-method.md) determines whether the variant contains a text variable. The return value is **false** because the variant does not contain a text.
   
```al
var
    MyCode: Code[100];
    MyVariant: Variant;
    varResult: Boolean;
    Text000: Label 'Does the variant >%1< contain a code variable? %2.';
    Text001: Label 'Does the variant >%1< contain a text variable? %2.';
begin
    MyCode := 'A1297';  
    MyVariant :=  MyCode;  
    varResult := MyVariant.IsCode;  
    Message(Text000,MyVariant,varResult);  
    varResult := MyVariant.IsText;  
    Message(Text001,MyVariant,varResult);  
end;
```  
  

## See Also
[Variant Data Type](variant-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)