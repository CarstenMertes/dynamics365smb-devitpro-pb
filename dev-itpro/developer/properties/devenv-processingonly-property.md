---
title: "ProcessingOnly Property"
description: "Sets the value that indicates whether a report produces printed output or only processes data."
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
# ProcessingOnly Property
> **Version**: _Available or changed with runtime version 1.0._

Sets the value that indicates whether a report produces printed output or only processes data.

## Applies to
-   Report

[//]: # (IMPORTANT: END>DO_NOT_EDIT)


## Property Value

**True** if you want a report that will not produce output; otherwise, **false**. The default is **false**. 

## Syntax

```AL
ProcessingOnly = true;
``` 
  
## Remarks  

When **ProcessingOnly** is set to **true**, then the **Advanced** tab on the request page is not shown. Use the **Report Limits** page instead.

> [!NOTE]  
> In versions before Business Central 2022 release wave 2, if **ProcessingOnly** is **true**, then the **Print** and **Preview** options on the request page are replaced by an **OK** button.
  
## See Also  

[Properties](devenv-properties.md)
