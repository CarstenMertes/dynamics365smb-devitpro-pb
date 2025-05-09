---
title: "BigInteger data type"
description: "Stores very large whole numbers that range from -9,223,372,036,854,775,807 to 9,223,372,036,854,775,807."
ms.author: solsen
ms.date: 02/18/2025
ms.topic: reference
author: SusanneWindfeldPedersen
ms.reviewer: solsen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# BigInteger Data type
> **Version**: _Available or changed with runtime version 1.0._

Stores very large whole numbers that range from -9,223,372,036,854,775,807 to 9,223,372,036,854,775,807.



## Instance methods
The following methods are available on instances of the BigInteger data type.

|Method name|Description|
|-----------|-----------|
|[ToText()](biginteger-totext-method.md)|Converts the value to a text. Equvilant to calling Format(value, 0, 0).|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  
 This data type is a 64-bit integer.  

 You must add an L to the constant definition to inform AL that the integer must be interpreted and treated as a BigInteger.  

 If you assign -9,223,372,036,854,775,808 directly to a BigInteger variable, then you get an error when you try to compile the code. However, you can indirectly assign -9,223,372,036,854,775,808 to a BigInteger variable by using the following code.  

```AL  
BigIntegerVar := -9223372036854775807L;  
BigIntegerVar := BigIntegerVar - 1;  
```  

 If you try to indirectly assign a value that is smaller than -9,223,372,036,854,775,808, or larger than 9,223,372,036,854,775,807, then you get a run-time error.  

## Example  

```AL  
BI := 1L;  
BI := 455500000000L;  
```  

## Related information

[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  