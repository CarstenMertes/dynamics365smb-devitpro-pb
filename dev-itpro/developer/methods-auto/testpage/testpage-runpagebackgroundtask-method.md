---
title: "TestPage.RunPageBackgroundTask(Integer [, var Dictionary of [Text, Text]] [, Boolean]) Method"
description: "Runs the page background task codeunit in the current session."
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
# TestPage.RunPageBackgroundTask(Integer [, var Dictionary of [Text, Text]] [, Boolean]) Method
> **Version**: _Available or changed with runtime version 4.0._

Runs the page background task codeunit in the current session. Note that by default, no triggers are invoked at this point.


## Syntax
```AL
Results :=   TestPage.RunPageBackgroundTask(CodeunitId: Integer [, var Parameters: Dictionary of [Text, Text]] [, RunCompletionTriggers: Boolean])
```
## Parameters
*TestPage*  
&emsp;Type: [TestPage](testpage-data-type.md)  
An instance of the [TestPage](testpage-data-type.md) data type.  

*CodeunitId*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
Specifies the ID of the codeunit to run.  
*[Optional] Parameters*  
&emsp;Type: [Dictionary of [Text, Text]](../dictionary/dictionary-data-type.md)  
Specifies a collection of keys and values that are passed to the OnRun trigger of the codeunit that runs when the page background task session is started.  
*[Optional] RunCompletionTriggers*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
Runs the completion triggers after the completion of the code unit. Default value is **false**.  


## Return Value
*Results*  
&emsp;Type: [Dictionary of [Text, Text]](../dictionary/dictionary-data-type.md)  
The dictionary of results for the page background task.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[TestPage Data Type](testpage-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)