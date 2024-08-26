---
title: "TestPart.GetField(Integer) Method"
description: "Gets a field on a test page."
ms.author: solsen
ms.date: 08/26/2024
ms.topic: reference
author: SusanneWindfeldPedersen
ms.reviewer: solsen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# TestPart.GetField(Integer) Method
> **Version**: _Available or changed with runtime version 3.0 until version 3.0 where it was deprecated._

Gets a field on a test page.


## Syntax
```AL
TestField :=   TestPart.GetField(Id: Integer)
```
## Parameters
*TestPart*  
&emsp;Type: [TestPart](testpart-data-type.md)  
An instance of the [TestPart](testpart-data-type.md) data type.  

*Id*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The ID of the field that you want to get.  


## Return Value
*TestField*  
&emsp;Type: [TestField](../testfield/testfield-data-type.md)  
The field on the test page.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[TestPart Data Type](testpart-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)