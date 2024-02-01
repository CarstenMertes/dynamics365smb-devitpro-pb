---
title: "Variant.IsAction() Method"
description: "Indicates whether an AL variant contains an Action variable."
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
# Variant.IsAction() Method
> **Version**: _Available or changed with runtime version 1.0._

Indicates whether an AL variant contains an Action variable.


## Syntax
```AL
Ok :=   Variant.IsAction()
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
**true** if the AL variant contains an Action variable, otherwise **false**.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Example  
 The following example determines whether an AL variant contains an Action variable. The MyAction variable is assigned to the variant variable that is named MyVariant. The **IsAction** method determines whether the variant contains an Action variable and stores the return value in the varResult variable. In this case, the variant contains an Action variable so **Yes** is returned and displayed in a message box. The [IsCode Method (Variant)](variant-iscode-method.md) determines whether the variant contains a code variable. The return value is **No** because the variant does not contain a code. 

```al
var
    MyAction: Action;
    MyVariant: Variant;
    varResult: Boolean;
    Text000: Label 'Does the variant contain an Action variable? %1.';
    Text001: Label 'Does the variant- contain a code variable? %1.';
begin
    MyVariant := MyAction;  
    varResult := MyVariant.IsAction;  
    Message(Text000,varResult);  
    varResult := MyVariant.IsCode;  
    Message(Text001, varResult);  
end;
```  
  

## See Also
[Variant Data Type](variant-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)