---
title: "Page.ObjectId([Boolean]) Method"
description: "Returns a string in the Page xxx format, where xxx is the caption or ID of the application object."
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
# Page.ObjectId([Boolean]) Method
> **Version**: _Available or changed with runtime version 1.0._

Returns a string in the "Page xxx" format, where xxx is the caption or ID of the application object.


## Syntax
```AL
String :=   Page.ObjectId([UseNames: Boolean])
```
## Parameters
*Page*  
&emsp;Type: [Page](page-data-type.md)  
An instance of the [Page](page-data-type.md) data type.  

*[Optional] UseNames*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** returns the page caption, if there is one; otherwise, it returns the page name. **false** returns the page ID as text.  


## Return Value
*String*  
&emsp;Type: [Text](../text/text-data-type.md)  
The text of the object


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Example

If you add the following code to a page method or trigger, then the returned string is displayed in a message window.  
  
```al
Message(CurrPage.ObjectId(true));  
  
```

CurrPage is a system-defined variable. For more information, see [System-Defined Variables](../../devenv-system-defined-variables.md). 

## See Also
[Page Data Type](page-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)