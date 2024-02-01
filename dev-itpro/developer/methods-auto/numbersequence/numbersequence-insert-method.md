---
title: "NumberSequence.Insert(Text [, BigInteger] [, BigInteger] [, Boolean]) Method"
description: "Creates a number sequence in the database, with the given parameters."
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
# NumberSequence.Insert(Text [, BigInteger] [, BigInteger] [, Boolean]) Method
> **Version**: _Available or changed with runtime version 4.0._

Creates a number sequence in the database, with the given parameters.


## Syntax
```AL
 NumberSequence.Insert(Name: Text [, Seed: BigInteger] [, Increment: BigInteger] [, CompanySpecific: Boolean])
```
## Parameters
*Name*  
&emsp;Type: [Text](../text/text-data-type.md)  
Specifies the name of the number sequence.  

*[Optional] Seed*  
&emsp;Type: [BigInteger](../biginteger/biginteger-data-type.md)  
Specifies the first value coming from the number sequence. Default is 0.  

*[Optional] Increment*  
&emsp;Type: [BigInteger](../biginteger/biginteger-data-type.md)  
The increment value used for the number sequence. Default is 1.  

*[Optional] CompanySpecific*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
Specifies if the number sequence is company-specific. Default is true.  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Example
The following example creates the number sequence `MyNumberSequence` that starts at zero and increments by a value of ten. The number series is not company specific.
 
```al
NumberSequence.Insert('MyNumberSequence', 0, 10, false);
```
## See Also
[NumberSequence Data Type](numbersequence-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)