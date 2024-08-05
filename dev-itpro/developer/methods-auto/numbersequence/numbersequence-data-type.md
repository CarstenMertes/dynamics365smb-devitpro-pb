---
title: "NumberSequence Data Type"
description: "Is a complex data type for creating and managing number sequences in the database."
ms.author: solsen
ms.date: 05/14/2024
ms.topic: reference
author: SusanneWindfeldPedersen
ms.reviewer: solsen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# NumberSequence Data Type
> **Version**: _Available or changed with runtime version 4.0._

Is a complex data type for creating and managing number sequences in the database.


## Static methods
The following methods are available on the NumberSequence data type.


|Method name|Description|
|-----------|-----------|
|[Current(Text [, Boolean])](numbersequence-current-method.md)|Gets the current value from the number sequence, without doing any increment. The value is retrieved out of transaction. The value will not be returned on transaction rollback.|
|[Delete(Text [, Boolean])](numbersequence-delete-method.md)|Deletes a specific number sequence.|
|[Exists(Text [, Boolean])](numbersequence-exists-method.md)|Checks whether a specific number sequence exists.|
|[Insert(Text [, BigInteger] [, BigInteger] [, Boolean])](numbersequence-insert-method.md)|Creates a number sequence in the database, with the given parameters.|
|[Next(Text [, Boolean])](numbersequence-next-method.md)|Retrieves the next value from the number sequence.|
|[Range(Text, Integer [, Boolean])](numbersequence-range-string-integer-boolean-method.md)|Retrieves a range of values from the number sequence.|
|[Range(Text, Integer, var BigInteger [, Boolean])](numbersequence-range-string-integer-biginteger-boolean-method.md)|Retrieves a range of values from the number sequence.|
|[Restart(Text [, BigInteger] [, Boolean])](numbersequence-restart-method.md)|Restarts a number sequence.|


[//]: # (IMPORTANT: END>DO_NOT_EDIT)


## See Also  
[Using number sequences](../../devenv-number-sequences.md)  
[Get atarted with AL](../../devenv-get-started.md)  
[Developing extensions](../../devenv-dev-overview.md)  
