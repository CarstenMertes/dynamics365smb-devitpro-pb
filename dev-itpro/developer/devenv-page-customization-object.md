---
title: Page customization object
description: The page customization object in Business Central allows you to add changes to the layout and actions on page that are accessible for a profile.
author: SusanneWindfeldPedersen
ms.date: 01/30/2025
ms.topic: how-to
ms.author: solsen
ms.reviewer: solsen
---

# Page customization object

The page customization object in [!INCLUDE [prod_short](includes/prod_short.md)] allows you to add changes to the layout and actions on page that are accessible for a profile. The page customization object has more restrictions than the [page extension object](devenv-page-ext-object.md); when you define a new page customization object, you can't add variables, procedures, or triggers. You can add actions, fields, and groups to the page customization object.

Learn how to use specific keywords to change the page customization layout in [Using keywords to place actions and controls](devenv-page-ext-object.md#using-keywords-to-place-actions-and-controls).


> [!NOTE]  
> A single page customization can be used with multiple profiles within the same extension. Page customizations only apply to the RoleCenters they're specified for. In order to view or changes the RoleCenters in the client, go to **My Settings**, and then choose **Role Center**. 

> [!NOTE]  
> Extension objects can have a name with a maximum length of 30 characters.

> [!NOTE]  
> Modifying actions in Cue groups on page extensions isn't supported.

> [!NOTE]  
> The property `allowDebugging`, which is a setting under `resourceExposurePolicy` doesn't apply to page customizations. Page customizations defined in an extension with `allowDebugging` set to `false` can still be copied using Designer. Learn more in [Resource exposure policy setting](devenv-security-settings-and-ip-protection.md).


## Snippet support

Typing the shortcut `tpagecust` creates the basic layout for a page customization object when using the [!INCLUDE[d365al_ext_md](../includes/d365al_ext_md.md)] in Visual Studio Code.

[!INCLUDE[intelli_shortcut](includes/intelli_shortcut.md)]

## Views

Views in [!INCLUDE [prod_short](includes/prod_short.md)] are used on list pages to define a different view of the data on a given page. Views can be defined for [Pages](devenv-page-object.md), [Page Extensions](devenv-page-ext-object.md), and [Page Customizations](devenv-page-customization-object.md). Learn more in [Views](devenv-views.md).


## Page customization example

The following page customization example `MyCustomization` makes changes to **Customer List**. By using the `moveafter` method, `Blanket Orders` is moved after the `Orders` action item. And the `modify` method is used to hide the `NewSalesBlanketOrder` action item.

```AL
profile TheBoss
{
    Description = 'The Boss';
    RoleCenter = "Business Manager Role Center";
    Customizations = MyCustomization;
    Caption = 'Boss';
}

pagecustomization MyCustomization customizes "Customer List"
{
    actions
    {
        moveafter(Orders; "Blanket Orders")

        modify(NewSalesBlanketOrder)
        {
            Visible = false;
        }

    }
}
```

You can use the same page customization on another profile within the same extension package by referencing its name from the profile definition, for example:

```AL
profile TheSalesman
{
    ProfileDescription = 'The Boss';
    RoleCenter = "Sales Manager Role Center";
    Customizations = MyCustomization;
    Caption = 'Salesman';
}
```

## Adding groups and page fields based on table fields

[!INCLUDE [2023-releasewave2](../includes/2023-releasewave2.md)]

You can add groups and page fields using a table field as source expression in page customizations as illustrated in the following example. 

```al
pagecustomization MyPageCust customizes MyPage
{
    layout
    {
        addfirst(Content)
        {
            field(MyPageCustField; Rec.MyTableField) {...}
        }
    }
}
```

To specify if a table field can be used as a source expression for page fields that are created in page customizations, use the [AllowInCustomizations](properties/devenv-allowincustomizations-property.md). The default behavior is that a table field *can* be used in such a way.


## Related information

[Developing extensions](devenv-dev-overview.md)  
[AL development environment](devenv-reference-overview.md)  
[Page object](devenv-page-object.md)  
[Page extension object](devenv-page-ext-object.md)  
[Views](devenv-views.md)  
[Page, page fields, and page extension properties](properties/devenv-page-property-overview.md)  
[AllowInCustomizations](properties/devenv-allowincustomizations-property.md)  
