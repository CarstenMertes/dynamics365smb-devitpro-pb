---
title: "AboutTitle Property"
description: "Sets the large-font title that appears in a teaching tip in the UI."
ms.author: solsen
ms.custom: na
ms.date: 09/06/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# AboutTitle Property
> **Version**: _Available or changed with runtime version 10.0._

Sets the large-font title that appears in a teaching tip in the UI.

## Applies to
-   Page Custom Action
-   Query
-   Page
-   Page Action
-   Page Action Group
-   Page Field
-   Page Part
-   Page Group
-   Request Page

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

- When setting this property, you must also set the [AboutText property](devenv-abouttext-property.md). Both About properties must be specified for the teaching tip to appear.
- The property is ignored at runtime if the current client is not the Web client.
- When setting this property on page objects:  
  - The page teaching tip is not displayed if the page has `PageType` set to `RoleCenter`, `NavigatePage`, `ConfirmationDialog`, `StandardDialog`, or `HeadlinePart`.
  
    Enable UICop rule [AW0012](../analyzers/uicop-aw0012.md) to prevent this at compile-time. 
  - The page teaching tip is not displayed automatically if the page is run in lookup mode, but it can still be reached from the page caption. Examples include pages run as an advanced lookup, and pages run with `LookupMode` set to `true`.  

- When setting this property on page controls:  
  - The control teaching tip is not shown if the control has a `Visible` property that evaluates to `false`. 
  - The control teaching tip is displayed for field controls only if they represent repeater fields or fields in the content area of the page. It is not displayed for other uses of field controls, such as cues. 
  - The control teaching tip is displayed for actions and action groups on the primary page. It is not displayed for other uses of actions, such as actions on page parts, action tiles, actions displayed in the footer of a `NavigatePage`, RoleCenter navigation menus, or actions displayed in the menu for a record in a list.
  - If the page object is a part that is embedded on the hosting page or in a FactBox, the control teaching tip becomes part of the tour on the hosting page. If the part is hosted on a Role Center, then the teaching tip is not displayed. 

[!INCLUDE[aboutTeachingTips](../includes/include-about-teaching-tips.md)]

## Example

```al
AboutTitle = 'About sales invoices'; 
```

## See Also  
[Teaching tips and in-app tours for onboarding users](../../administration/onboarding-teaching-tips-tours.md)  
[Get Started with AL](../devenv-get-started.md)  
[Developing Extensions](../devenv-dev-overview.md)  
[AboutText Property](devenv-abouttext-property.md)