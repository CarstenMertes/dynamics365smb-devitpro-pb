---
title: "TestField.GetValidationError([Integer]) Method"
description: "Gets the validation error that occurred on a test page."
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
# TestField.GetValidationError([Integer]) Method
> **Version**: _Available or changed with runtime version 1.0._

Gets the validation error that occurred on a test page.


## Syntax
```AL
Result :=   TestField.GetValidationError([Index: Integer])
```
## Parameters
*TestField*  
&emsp;Type: [TestField](testfield-data-type.md)  
An instance of the [TestField](testfield-data-type.md) data type.  

*[Optional] Index*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The index of the validation error that occurred on the test page.  


## Return Value
*Result*  
&emsp;Type: [Text](../text/text-data-type.md)  
The validation error that occurred on a test page.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[TestField Data Type](testfield-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)