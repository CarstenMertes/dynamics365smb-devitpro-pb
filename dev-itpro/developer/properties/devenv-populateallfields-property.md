---
title: "PopulateAllFields property"
description: "Sets whether fields are filled out automatically with a single filter value when a new record is inserted in a table."
ms.author: solsen
ms.date: 02/18/2025
ms.topic: reference
author: SusanneWindfeldPedersen
ms.reviewer: solsen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# PopulateAllFields Property
> **Version**: _Available or changed with runtime version 1.0._

Sets whether fields are filled out automatically with a single filter value when a new record is inserted in a table.

## Applies to
-   Request Page
-   Page

[//]: # (IMPORTANT: END>DO_NOT_EDIT)


## Property Value

 **True** if you want the fields filled out automatically; otherwise, **false**. The default is **false**.  

## Syntax

```AL
PopulateAllFields = true;
``` 

## Remarks

Values are inserted in those fields where a currently active filter expression evaluates to exactly one value. Key fields are always populated.  
  
## Related information  

[Properties](devenv-properties.md)