---
title: "Variant.IsBoolean() Method"
description: "Indicates whether an AL variant contains a Boolean variable."
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
# Variant.IsBoolean() Method
> **Version**: _Available or changed with runtime version 1.0._

Indicates whether an AL variant contains a Boolean variable.


## Syntax
```AL
Ok :=   Variant.IsBoolean()
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
**true** if the AL variant contains a Boolean variable, otherwise **false**.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Example  
 The following example determines whether an AL variant contains a Boolean variable. The code initializes the MyBoolean variable with a Boolean value. The MyBoolean variable is assigned to the variant variable that is named MyVariant. The **IsBoolean** method determines whether the variant contains a Boolean variable and stores the return value in the varResult variable. In this case, the variant contains a Boolean variable so **true** is returned and displayed in a message box. The Boolean value is obtained from the **Critical** field in the **Item** table. The [IsCode Method (Variant)](variant-iscode-method.md) determines whether the variant contains a code variable. The return value is **false** because the variant does not contain a code. 
  
```al  
var
    ItemRec: Record Item;
    MyBoolean: Boolean;
    MyVariant: Variant;
    varResult: Boolean;
    Text000: Label 'Does the variant >%1< contain a Boolean variable? %2.';
    Text001: Label 'Does the variant >%1< contain a code variable? %2.';
begin
    MyBoolean := ItemRec.Critical;  
    MyVariant := MyBoolean;  
    varResult := MyVariant.IsBoolean;  
    Message(Text000,MyVariant,varResult);  
    varResult := MyVariant.IsCode;  
    Message(Text001,MyVariant,varResult);  
end;
```  

## See Also
[Variant Data Type](variant-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)