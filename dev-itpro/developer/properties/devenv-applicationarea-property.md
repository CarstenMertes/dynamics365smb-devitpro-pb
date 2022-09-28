---
title: "ApplicationArea Property"
description: "Sets the application areas that apply to the control."
ms.author: solsen
ms.custom: na
ms.date: 08/22/2022
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# ApplicationArea Property
> **Version**: _Available or changed with runtime version 1.0._

Sets the application areas that apply to the control. Standard values are All, Basic, Suite, and Advanced.

## Applies to
-   Page Label
-   Page Field
-   Page Part
-   Page System Part
-   Page Chart Part
-   Page Action
-   Page Custom Action
-   Page User Control
-   Page
-   Report

[//]: # (IMPORTANT: END>DO_NOT_EDIT)


## Property Values

A text string that contains a comma-separated list of application area tags.  
  
An application area tag must have the format *name*, where *name* is the application area. The *name* can be any combination of letters (Aa-Zz) and numbers (0-9) without spaces. For example, to specify the **Basic** and **Fixed Assets** application areas, set the property to **Basic, FixedAssets**.  
  
If the control applies to all application areas, you can set the property to **All**. This means that the control will always appear in the user interface.  
 
## Syntax

```AL
ApplicationArea = Basic, Suite;
```

## Remarks

[!INCLUDE [2022_releasewave2](../../includes/2022_releasewave2.md)]

With [!INCLUDE [prod_short](../includes/prod_short.md)] 2022 release wave 2, the `ApplicationArea` property set on fields defaults to the page value. The property inheritance means that page controls without the `ApplicationArea` property explicitly set, inherit the `ApplicationArea` *defined on the parent page* or *report if it's a request page*. The `ApplicationArea` property can be used without setting the `UsageCategory` property on pages to provide a default fallback for controls, without forcing search visibility.

> [!NOTE]  
> The `ApplicationArea` property inheritance has *no impact on page or report extensions*. On these extensions values must still be set explicitly.

Application areas represent a feature in the system that offers developers, administrators, and users the ability to define differentiated user experiences. They are mapped to controls to show or hide them on page objects to enable more or fewer business scenarios.

The **ApplicationArea** property is used together with the [ApplicationArea method](../methods-auto/session/session-applicationarea-method.md) to hide user interface elements.  
  
If one or more application areas are enabled in a session, any controls that are not tagged with an application area will not appear in the user interface. 

You can also add new application areas, see [Extending Application Areas](../devenv-extending-application-areas.md) for more information.

## Dependent Property

The **UsageCategory** property is a required setting used together with the **ApplicationArea** property. This enables a page or a report to be available in Search for the navigation support. For more information about navigation support, see [Adding Pages and Reports to Search](../devenv-al-menusuite-functionality.md).  
   
## See Also  

[ApplicationArea Method](../methods-auto/session/session-applicationarea-method.md)  
[Extending Application Areas](../devenv-extending-application-areas.md)  
[AccessByPermission Property](devenv-accessbypermission-property.md)  
[Properties](devenv-properties.md)