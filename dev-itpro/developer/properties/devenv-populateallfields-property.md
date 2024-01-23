---
title: "PopulateAllFields Property"
description: "Sets whether fields are filled out automatically with a single filter value when a new record is inserted in a table."
ms.author: solsen
ms.custom: na
ms.date: 06/15/2022
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# PopulateAllFields Property
> **Version**: _Available or changed with runtime version 1.0._

Sets whether fields are filled out automatically with a single filter value when a new record is inserted in a table.

## Applies to
-   Page
-   Request Page

[//]: # (IMPORTANT: END>DO_NOT_EDIT)


## Property Value

 **True** if you want the fields filled out automatically; otherwise, **false**. The default is **false**.  

## Syntax

```AL
PopulateAllFields = true;
``` 

## Remarks

Values are inserted in those fields where a currently active filter expression evaluates to exactly one value. Key fields are always populated.  
  
## See Also  

[Properties](devenv-properties.md)