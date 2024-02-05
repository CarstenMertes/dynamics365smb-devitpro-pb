---
title: "OnAfterGetRecord (Xml Port Table Element) Trigger"
description: "Runs after a record is retrieved from a table and before it is exported to the XML document."
ms.author: solsen
ms.custom: na
ms.date: 06/23/2021
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)

# OnAfterGetRecord (Xml Port Table Element) Trigger
> **Version**: _Available or changed with runtime version 1.0._

Runs after a record is retrieved from a table and before it is exported to the XML document.


## Syntax
```AL
trigger OnAfterGetRecord()
begin
    ...
end;
```



[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  
 This trigger is only used to export data. It is typically used to manipulate the fields that are being exported from the table and to calculate the variables that depend on the record.  

## See Also  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  
[OnAfterGetRecord (Page) Trigger](../page/devenv-onaftergetrecord-page-trigger.md)  
[OnAfterGetRecord (Request Page) Trigger](../requestpage/devenv-onaftergetrecord-requestpage-trigger.md)  
[OnAfterGetRecord (Request Page Extension) Trigger](../requestpageextension/devenv-onaftergetrecord-requestpageextension-trigger.md)  
[OnAfterGetRecord (Page Extension) Trigger](../pageextension/devenv-onaftergetrecord-pageextension-trigger.md)  
[OnAfterGetRecord (Report Data Item) Trigger](../reportdataitem/devenv-onaftergetrecord-reportdataitem-trigger.md)
