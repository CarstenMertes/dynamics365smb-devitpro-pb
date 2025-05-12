---
title: "Page.LookupMode([Boolean]) Method"
description: "Gets or sets the default lookup mode for the page."
ms.author: solsen
ms.date: 08/26/2024
ms.topic: reference
author: SusanneWindfeldPedersen
ms.reviewer: solsen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Page.LookupMode([Boolean]) Method
> **Version**: _Available or changed with runtime version 1.0._

Gets or sets the default lookup mode for the page.


## Syntax
```AL
[LookupMode := ]  Page.LookupMode([NewLookupMode: Boolean])
```
> [!NOTE]
> This method can be invoked using property access syntax.
## Parameters
*Page*  
&emsp;Type: [Page](page-data-type.md)  
An instance of the [Page](page-data-type.md) data type.  

*[Optional] NewLookupMode*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
The new default lookup mode for the page.  


## Return Value
*[Optional] LookupMode*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
The current default lookup mode for the page


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

The `LookupMode` method gets or sets the default lookup mode for the page. The lookup mode determines how the page behaves when a user selects a record in a lookup. If the default lookup mode is `false`, the page opens the selected record in the same window. If the lookup mode is set to `true`, the page opens the selected record in a new window.

## Related information

[Page Data Type](page-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)