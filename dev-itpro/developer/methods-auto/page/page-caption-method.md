---
title: "Page.Caption([Text]) Method"
description: "The caption shown in the title bar."
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
# Page.Caption([Text]) Method
> **Version**: _Available or changed with runtime version 1.0._

The caption shown in the title bar. For example, the default value in English (United States) is the same as the name of the page.


## Syntax
```AL
[Caption := ]  Page.Caption([NewCaption: Text])
```
> [!NOTE]
> This method can be invoked using property access syntax.
## Parameters
*Page*  
&emsp;Type: [Page](page-data-type.md)  
An instance of the [Page](page-data-type.md) data type.  

*[Optional] NewCaption*  
&emsp;Type: [Text](../text/text-data-type.md)  
The new caption text.  


## Return Value
*[Optional] Caption*  
&emsp;Type: [Text](../text/text-data-type.md)  
The text used for the caption.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[Page Data Type](page-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)