---
title: "Database.Commit() Method"
description: "Ends the current write transaction."
ms.author: solsen
ms.date: 08/26/2024
ms.topic: reference
author: SusanneWindfeldPedersen
ms.reviewer: solsen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Database.Commit() Method
> **Version**: _Available or changed with runtime version 1.0._

Ends the current write transaction.


## Syntax
```AL
 Database.Commit()
```
> [!NOTE]
> This method can be invoked without specifying the data type name.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

During AL code execution, if a transaction is needed, the AL runtime automatically initializes it. At the completion of AL code execution, any transactions that are created are also automatically ended, committing any updates made by the AL code.

This means that if you want code execution to perform a single write transaction, it's automatically handled for you. However, if you want the code execution to perform multiple write transactions, you must use the `Commit` method to end one write transaction before you can start the next. The `Commit` method separates write transactions in an AL code module.

## Example

The following pseudo-code example contains two write transactions. When it begins, a write transaction is automatically started. Using the Commit method, you end the first write transaction and prepare for the second. When the code completes, the second write transaction automatically ends.  

```  
BeginWriteTransactions  
(AL Statements) // Transaction 1  
Commit();  
(AL Statements) // Transaction 2  
EndWriteTransactions   
```  

## Related information

[Database Data Type](database-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)