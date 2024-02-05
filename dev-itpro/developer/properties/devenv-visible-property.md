---
title: "Visible Property"
description: "Sets whether to display the page or control."
ms.author: solsen
ms.custom: na
ms.date: 08/04/2022
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Visible Property
> **Version**: _Available or changed with runtime version 1.0._

Sets whether to display the page or control.

## Applies to
-   Page Label
-   Page Field
-   Page Group
-   Page Part
-   Page System Part
-   Page Chart Part
-   Page Action
-   Page Action Group
-   Page Action Ref
-   Page Custom Action
-   Page View
-   Page User Control

[//]: # (IMPORTANT: END>DO_NOT_EDIT)


## Property value  

**True** on pages if you want the page or control to be visible; otherwise, **false** on pages. The default is **true** on pages.  

## Syntax

```AL
Visible = false;
```

## Remarks  

Because this property also applies to containers, such as pages and subpages, if the **Visible** property for the container is set to **false**, then controls on the container are also not displayed, even if the **Visible** property is set to **true**.  

### Dynamic visibility of controls

> [!NOTE]  
> You can also use as property value a **Boolean** variable that evaluates to **true** or **false**. To use a variable for the **Visible** property, it must be set as a global page variable and the [InDataSet attribute](../attributes/devenv-indataset-attribute.md) must be defined on the variable.   

On pages, you use the **Visible** property to show or hide group, part, field, and action controls. You can show or hide the control either statically by setting the property to **true** or **false**, or dynamically by using a Boolean variable or a Boolean field on the page. The Boolean field on the page can be either a true/false Boolean or a Boolean expression, such as "Credit Limit > Sales YTD".  

> [!NOTE]  
> The dynamic options are only possible for group, part, and action controls.  

Using a variable for field and action controls requires that the variable be resolved by the [OnInit Trigger](../triggers-auto/page/devenv-oninit-page-trigger.md) or [OnOpenPage Trigger](../triggers-auto/page/devenv-onopenpage-page-trigger.md).  


### UI customization and visibility of controls

When a part, field, action, or view is hidden by setting the **Visible** property, users are able to access and display that control again using personalization and role customization features in the user interface. The **Visible** property is not a replacement for user permissions or the application of proper security practices.  

When the **Visible** property is specified by a Boolean variable, users can choose to hide the control while the Boolean evaluates to true, but cannot forcibly show the control while the control Boolean evaluates to false.

### Loading of data

Even if a field on page is hidden by setting the **Visible** property, the data behind the field will still be loaded.

> [!NOTE]  
> Hidden record fields on a page that calculates data such as FlowFields can lead to performance issues even if they are hidden. For more information see [Writing efficient pages](../../performance/performance-developer.md#writing-efficient-pages).

## See also

[Properties](devenv-properties.md)  
[InDataSet Property](devenv-indataset-property.md)  
[Performance Developer](../../performance/performance-developer.md)  
