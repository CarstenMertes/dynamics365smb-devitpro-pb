---
title: "OnLookup (Field) Trigger"
description: "Runs when a lookup page is displayed."
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

# OnLookup (Field) Trigger
> **Version**: _Available or changed with runtime version 1.0._

Runs when a lookup page is displayed.


## Syntax
```AL
trigger OnLookup()
begin
    ...
end;
```



[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  

The [Lookup Property](../../properties/devenv-lookup-property.md) must be set to **True** to enable the lookup.

There are three lookup options:  

1. Default Lookup - The lookup into the table is performed without applying filters or other special parameters.  
2. Field Lookup - You can use this trigger to define a field lookup that will be used in place of the default lookup.  
3. Text box Lookup - You can use the [OnLookup \(Page fields\) Trigger](../pagefield/devenv-onlookup-pagefield-trigger.md) to define a lookup based on the value of a text box. This value will be used in place of the default lookup or the field lookup.  

When using this trigger, follow this approach:  

- Use the field value to determine what filters or other parameters to apply.  

- Run the lookup page as a modal page.  

- Transfer the value the user selects back to the field when the user chooses **OK**.  

 If an error occurs in the trigger code, the lookup page is closed.  

<!--NAV  
> [!NOTE]  
>  On non-editable fields in the [!INCLUDE[nav_windows](../includes/nav_windows_md.md)], the field gets its lookup action rendered as a hyperlink. In the [!INCLUDE[nav_web](../includes/nav_web_md.md)] the lookup for a non-editable field is not rendered. You can use the [OnDrillDown Trigger](devenv-OnDrillDown-Trigger.md) instead.  
-->
> [!NOTE]  
> The lookup for a non-editable field is not rendered. You can use the [OnDrillDown Trigger](../pagefield/devenv-ondrilldown-pagefield-trigger.md) instead.

## See Also  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  
[OnLookup (Page Field) Trigger](../pagefield/devenv-onlookup-pagefield-trigger.md)  
[OnLookup (Page Field Extension) Trigger](../pagefieldextension/devenv-onlookup-pagefieldextension-trigger.md)
