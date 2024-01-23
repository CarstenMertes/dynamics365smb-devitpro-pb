---
title: "NumberSequence.Next(Text [, Boolean]) Method"
description: "Retrieves the next value from the number sequence."
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
# NumberSequence.Next(Text [, Boolean]) Method
> **Version**: _Available or changed with runtime version 4.0._

Retrieves the next value from the number sequence.


## Syntax
```AL
Next :=   NumberSequence.Next(Name: Text [, CompanySpecific: Boolean])
```
## Parameters
*Name*  
&emsp;Type: [Text](../text/text-data-type.md)  
Specifies the name of the number sequence.  

*[Optional] CompanySpecific*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
Specifies if the number sequence is company-specific. Default is true.  


## Return Value
*Next*  
&emsp;Type: [BigInteger](../biginteger/biginteger-data-type.md)  
Returns the next value from number sequence.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Example
The following example gets the next value in the number sequence `MyNumberSequence`. The number series is not company specific.
 
```al
number := NumberSequence.Next('MyNumberSequence', false);
```

## See Also
[NumberSequence Data Type](numbersequence-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)