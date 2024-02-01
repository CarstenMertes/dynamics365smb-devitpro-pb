---
title: "Dialog.LogInternalError(Text, Text, DataClassification, Verbosity) Method"
description: "Log internal errors for telemetry."
ms.author: solsen
ms.custom: na
ms.date: 03/02/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Dialog.LogInternalError(Text, Text, DataClassification, Verbosity) Method
> **Version**: _Available or changed with runtime version 6.0._

Log internal errors for telemetry.

> [!NOTE]
> This method is supported only in Business Central on-premises.

## Syntax
```AL
 Dialog.LogInternalError(Message: Text, SubstitutionString: Text, DataClassificationInstance: DataClassification, VerbosityInstance: Verbosity)
```
> [!NOTE]
> This method can be invoked without specifying the data type name.
## Parameters
*Message*  
&emsp;Type: [Text](../text/text-data-type.md)  
This string contains the text of the error message you want to log into telemetry. Use a percent sign (%) to insert a variable value into the string. Place the percent where you want the system to substitute the variable value. You may only insert one variable value. It is not what the user will get, they will only get a generic error message.  

*SubstitutionString*  
&emsp;Type: [Text](../text/text-data-type.md)  
This string replaces a percent sign in the "Message" Parameter.  

*DataClassificationInstance*  
&emsp;Type: [DataClassification](../dataclassification/dataclassification-option.md)  
Sets the classification of the data in the error message.  

*VerbosityInstance*  
&emsp;Type: [Verbosity](../verbosity/verbosity-option.md)  
Represents the security level of events.  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[Dialog Data Type](dialog-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)