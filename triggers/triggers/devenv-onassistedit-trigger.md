---
title: "OnAssistEdit Trigger"
description: "OnAssistEdit trigger in AL for Business Central."
ms.date: 04/01/2021
ms.topic: reference
author: SusanneWindfeldPedersen
---

# OnAssistEdit Trigger

Runs in place of the [AssistEdit Property](../properties/devenv-assistedit-property.md) features that are provided in the application.  

## Syntax  

```AL
trigger OnAssistEdit()
begin
    ...
end;
``` 

## Applies to

- Fields on pages  

> [!NOTE]  
> The trigger is not invoked on a page that is in view mode<!--NAV in the [!INCLUDE[nav_web](../includes/nav_web_md.md)]-->.  

## Remarks

The [AssistEdit Property](../properties/devenv-assistedit-property.md) must be set to **True** to enable the assist-edit capabilities.

If there is an error in the trigger code, then the page is closed.  

You can use this trigger to write to the database.  

## See Also  

[Triggers](devenv-triggers.md)  
[AssistEdit Property](../properties/devenv-assistedit-property.md)  
[Page and Action Triggers](devenv-page-and-action-triggers.md)  
[Page Properties](../properties/devenv-properties.md)