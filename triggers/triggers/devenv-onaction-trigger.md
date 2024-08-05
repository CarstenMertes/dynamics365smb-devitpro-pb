---
title: "OnAction Trigger"
description: "OnAction trigger in AL for Business Central."
ms.date: 04/01/2021
ms.topic: reference
author: SusanneWindfeldPedersen
---

# OnAction Trigger

Runs when a user selects an action on a page.  

## Syntax  

```AL
trigger OnAction()
begin
    ...
end;
```

## Applies to  

- Page actions  

## Remarks

This is called after the action properties, such as the [RunObject Property](../properties/devenv-runobject-property.md), are invoked.  

You typically use the [RunObject Property](../properties/devenv-runobject-property.md) to run objects such as pages, reports, and codeunits from an action. You can use the OnAction trigger when you require more processing than the [RunObject Property](../properties/devenv-runobject-property.md) can support, such as filtering data before a page is displayed or writing to the database.  

> [!NOTE]  
> The OnAction trigger is not used on Role Center pages. If you add AL code to the trigger, the Role Center page will compile, but the AL code will be ignored at runtime.  

## See Also

[RunObject Property](../properties/devenv-runobject-property.md)  
[Page and Action Triggers](devenv-page-and-action-triggers.md)  
[Page Properties](../properties/devenv-properties.md)  
[Triggers](devenv-triggers.md)