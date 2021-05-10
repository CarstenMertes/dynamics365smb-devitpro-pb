---
title: "OnClosePage (Page Extension) Trigger"
description: "Runs as a page closes after the OnQueryClosePage trigger is run."
ms.author: solsen
ms.custom: na
ms.date: 04/27/2021
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: reference
ms.service: "dynamics365-business-central"
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)

# OnClosePage (Page Extension) Trigger
> **Version**: _Available or changed with runtime version 1.0._

Runs as a page closes after the OnQueryClosePage trigger is run.


## Syntax
```
trigger OnClosePage()
begin
    ...
end;
```



[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

> [!IMPORTANT]  
> The trigger is only invoked when the page is hosted in a modal popup window \(MPO\).

This trigger is initiated by a user action, such as when the user chooses the **Close** button, or by the CurrPage.CLOSE  being called.  

You can write to the database from this trigger.

## See Also  
[Getting Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  
[OnClosePage (Page) Trigger](../page/devenv-onclosepage-page-trigger.md)  
[OnClosePage (Request Page) Trigger](../requestpage/devenv-onclosepage-requestpage-trigger.md)  
[OnClosePage (Request Page Extension) Trigger](../requestpageextension/devenv-onclosepage-requestpageextension-trigger.md)