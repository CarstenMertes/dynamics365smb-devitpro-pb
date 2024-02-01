---
title: "System.GlobalLanguage([Integer]) Method"
description: "Gets and sets the current global language setting."
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
# System.GlobalLanguage([Integer]) Method
> **Version**: _Available or changed with runtime version 1.0._

Gets and sets the current global language setting.


## Syntax
```AL
[LanguageID := ]  System.GlobalLanguage([NewLanguageID: Integer])
```
> [!NOTE]
> This method can be invoked using property access syntax.
> [!NOTE]
> This method can be invoked without specifying the data type name.
## Parameters
*[Optional] NewLanguageID*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The Microsoft language ID (LCID), such as 1033 for English (US).  


## Return Value
*[Optional] LanguageID*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The Microsoft language ID (LCID).


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

The LanguageID is a standard Windows language ID. The Windows Language virtual table contains a list of these IDs and the corresponding names and short names.  
  
For more information, see [Multilanguage Development](../../devenv-work-with-translation-files.md). 
 
## See Also
[System Data Type](system-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)