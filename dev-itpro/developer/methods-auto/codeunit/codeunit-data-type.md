---
title: "Codeunit Data Type"
description: "Is a container for AL code that you can use from other application objects."
ms.author: solsen
ms.custom: na
ms.date: 12/01/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Codeunit Data Type
> **Version**: _Available or changed with runtime version 1.0._

Is a container for AL code that you can use from other application objects.


## Static methods
The following methods are available on the Codeunit data type.


|Method name|Description|
|-----------|-----------|
|[Run(Integer [, var Record])](codeunit-run-method.md)|Loads and runs the unit of AL code you specify. To use this method, you can specify a table associated with the codeunit when you defined the codeunit properties. This allows you to pass a variable with the method. The transaction that the codeunit contains is always committed due to the Boolean return value.|

## Instance methods
The following methods are available on instances of the Codeunit data type.

|Method name|Description|
|-----------|-----------|
|[Run(var Record)](codeunitinstance-run-method.md)|Loads and executes the unit of AL code that you specify.|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  