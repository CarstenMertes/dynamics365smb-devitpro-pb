---
title: "Promoted (Action) Property"
description: "Sets the value that indicates whether the selected action is elevated to a promoted category in the action bar."
ms.custom: na
ms.date: 07/08/2021
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---

# Promoted (Action) Property

> **Version**: _Available from runtime version 1.0._

<!-- this topic is manually created, parent node is devenv-promoted-property.md -->

Sets the value that indicates whether the selected action is promoted, which means that it is elevated to a promoted category in the action bar, as well as the group where is it defined. **Promoted** can also be set on Profiles, see [Promoted (Profiles) Property](devenv-promoted-profile-property.md).

> [!NOTE]  
> With [!INCLUDE [prod_short](../includes/prod_short.md)] 2022 release wave 2, the way that you promote actions on pages or page extensions has changed. Promoting actions is defined in a specific section of the page definition and contains a reference to the action. For more information, see [Promoted Actions](../devenv-promoted-actions.md).

> [!NOTE]  
> Removing the Promoted property on a published action is considered a breaking change. For more information, see [AppSourceCop Error AS0031](../analyzers/appsourcecop-as0031.md) and [UICop Warning AW0013](../analyzers/uicop-aw0013.md).

  
## Applies to  
  
- Page actions  

## Property Value

**true** promotes the action; otherwise **false**.
  
## Example

The following code illustrates how to set the **Promoted** property.
 
```AL
page 50110 PageName
{
    PageType = Card;

    actions
    {
        // Adds the action called "My Actions" to the Action menu 
        area(Processing)
        {
            action("My Actions")
            {
                Promoted = true;
                PromotedCategory = Process;
                ApplicationArea = All;

...
```

## Remarks

This feature allows you to make a copy of an action and place it on the on the action bar where it is easier to find. 

In order to specify where the promoted action should be placed, you must also set the [PromotedCategory property](devenv-promotedcategory-property.md).

For more information about promoting actions, see [Promoted Actions](../devenv-promoted-actions.md).

> [!NOTE]  
> The Promoted property only has an effect on actions defined in pages of type Card, Document, List, ListPlus and Worksheet. The Promoted property has also no effect on actions defined in cuegroups.

For more information about the Promoted property used together with the Scope property, see [Scope property](devenv-scope-action-property.md).

> [!NOTE] 
> On [!INCLUDE[d365fin_tablet_md](../includes/d365fin_tablet_md.md)] and [!INCLUDE[d365fin_phone_md](../includes/d365fin_phone_md.md)], only promoted actions are displayed.  
  
## See Also  

[PromotedIsBig Property](devenv-promotedisbig-property.md)  
[PromotedOnly Property](devenv-promotedonly-property.md)  
[Promoted (Profiles) Property](devenv-promoted-profile-property.md)
[Actions Overview](../devenv-actions-overview.md)  
