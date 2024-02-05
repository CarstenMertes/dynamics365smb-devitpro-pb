---
title: "System.GetLastErrorText() Method"
description: "Gets the last error that occurred in the debugger."
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
# System.GetLastErrorText() Method
> **Version**: _Available or changed with runtime version 1.0._

Gets the last error that occurred in the debugger.


## Syntax
```AL
String :=   System.GetLastErrorText()
```
> [!NOTE]
> This method can be invoked using property access syntax.
> [!NOTE]
> This method can be invoked without specifying the data type name.

## Return Value
*String*  
&emsp;Type: [Text](../text/text-data-type.md)  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

If you call the GetLastErrorText method immediately after you call the ClearLastError method, then an empty string is returned.  

The result of the [GetLastErrorCode Method](../../methods-auto/system/system-getlasterrorcode-method.md) is not translated into the local language. The result of the GetLastErrorText method is translated into the local language.  

## Example  

If you call the Codeunit.Run method to run a codeunit and an error occurs in the codeunit, then  the error is displayed. However, if you also use the return value of the Codeunit.Run method, then the error is not displayed. In this case, you can use the GetLastErrorText method to determine whether an error has occurred and to see the text of the last error message that was generated. This example shows how to use the GetLastErrorText method. This example requires that you create two codeunits. Codeunit 50001 generates an error. Codeunit 50002 runs codeunit 50001 and if an error occurs, then it displays the text of the error.  

```al
// Codeunit 50001  
// OnRun trigger  
Error(‘Some error message.’);  

// Codeunit 50002  
// OnRun trigger  
ClearLastError();  
if not Codeunit.Run(50001) then  
  Message(‘The last error was: ’ + GetLastErrorText);  
```  

In this example, because the if statement uses the return value of the Codeunit.Run method, the error from codeunit 50001 is not displayed. Instead, you use the GetLastErrorText method to display the error.  

When you run codeunit 50002, the message window displays the following:  

**The last error was: Some error message.**  
 
## See Also

[System Data Type](system-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)