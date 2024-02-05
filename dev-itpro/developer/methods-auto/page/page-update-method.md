---
title: "Page.Update([Boolean]) Method"
description: "Saves the current record and then updates the controls on the page."
ms.author: solsen
ms.custom: na
ms.date: 12/15/2021
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Page.Update([Boolean]) Method
> **Version**: _Available or changed with runtime version 1.0._

Saves the current record and then updates the controls on the page. If you set the SaveRecord parameter to false, this method will not save the record before the page is updated.


## Syntax
```AL
 Page.Update([SaveRecord: Boolean])
```
## Parameters
*Page*  
&emsp;Type: [Page](page-data-type.md)  
An instance of the [Page](page-data-type.md) data type.  

*[Optional] SaveRecord*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
Set this parameter to true if you want to save the current record. Set this parameter to false if you want to update without saving the current record.  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

The `SaveRecord` default depends on whether SourceTable is specified or not. If SourceTable is not defined (== null), then the default value is `false`. If SourceTable is specified then the default value is `true`.

## See Also

[Page Data Type](page-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)