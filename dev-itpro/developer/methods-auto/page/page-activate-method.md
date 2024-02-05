---
title: "Page.Activate([Boolean]) Method"
description: "Activates the current page on the client if possible."
ms.author: solsen
ms.custom: na
ms.date: 01/16/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Page.Activate([Boolean]) Method
> **Version**: _Available or changed with runtime version 1.0._

Activates the current page on the client if possible. The data on the page will not be refreshed.


## Syntax
```AL
[Ok := ]  Page.Activate([Refresh: Boolean])
```
## Parameters
*Page*  
&emsp;Type: [Page](page-data-type.md)  
An instance of the [Page](page-data-type.md) data type.  

*[Optional] Refresh*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
If set to **true**, the data on the page will be refreshed.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

The functionality of activating a page is no longer supported by the modern clients. Use `CurrPage.Update(false)` to keep the data update functionality.

## See Also
[Page Data Type](page-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)