---
title: "SessionInformation.SqlStatementsExecuted() Method"
description: "Gets the amount of SQL statements executed on the session, since the session started."
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
# SessionInformation.SqlStatementsExecuted() Method
> **Version**: _Available or changed with runtime version 4.0._

Gets the amount of SQL statements executed on the session, since the session started.


## Syntax
```AL
SqlStatementsExecuted :=   SessionInformation.SqlStatementsExecuted()
```
> [!NOTE]
> This method can be invoked using property access syntax.


## Return Value
*SqlStatementsExecuted*  
&emsp;Type: [BigInteger](../biginteger/biginteger-data-type.md)  
The amount of SQL statements executed on the session, since the session started.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

AL debugger also lets you to monitor the number of SQL statements executed. For more information, see [Debugging SQL behavior](../../devenv-debugging.md#DebugSQL).

## Example

The following code gets the number of SQL statements executed and displays the number in a message.

```al
var
    SqlStatementsExecuted : BigInteger;

begin

    SqlStatementsExecuted := SessionInformation.SqlStatementsExecuted();
    Message(Format(SqlStatementsExecuted));
end;
```

## See Also

[SessionInformation Data Type](sessioninformation-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)
