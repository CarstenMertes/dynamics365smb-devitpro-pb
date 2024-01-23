---
title: "Editable Property"
description: "Sets a value that indicates whether a field, page, or control can be edited through the UI."
ms.author: solsen
ms.custom: na
ms.date: 09/15/2022
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Editable Property
> **Version**: _Available or changed with runtime version 1.0._

Sets a value that indicates whether a field, page, or control can be edited through the UI.

## Applies to
-   Table Field
-   Page
-   Request Page
-   Page Label
-   Page Field
-   Page Group
-   Page System Part
-   Page Chart Part
-   Page Part

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Property Value

**True** on pages if the field, page, or control can be edited; otherwise, **false** on pages. The default value is **true**.  

## Syntax

```AL
Editable = true;
```

## Remarks

For fields, use this property to make a field for display only.  

For controls, if the **Editable** property for the container that contains this control is set to **false**, then that setting overrides what you enter here.  

If a page has **Editable** set to **false**, then the controls on the page aren't editable, even if the individual **Editable** properties are set to **true**.  

The property setting is checked during validation. Validation occurs only if the field or control value is updated through the UI. For example, when a value is updated on a page or when a field is updated in a table. If a field is updated through application code, then the **Editable** property isn't validated.  

> [!NOTE]  
> When using `CurrPage.Editable`, the **Editable** property also reflects the page mode that the page was opened in. This applies to Edit, Create, and Delete modes, but not to View mode. If the page not is editable, then `CurrPage.Editable` will return **false**.  

On pages, you use the **Editable** property for group, part, field, and action controls. You can make them editable or non-editable either statically by setting the property to **true** or **false**, or dynamically by using a Boolean variable or a Boolean field on the page. The Boolean field on the page can either be a Boolean value true/false or a Boolean expression. For a page showing the Customer table, an example could be:

```al
Editable = "Balance Due (LCY)" > "Credit Limit (LCY)"
```

> [!CAUTION]  
> Do not use `CurrPage.Editable` to prevent users from deleting entries. We recommend that you use permissions to control which users can delete data.  

> [!NOTE]  
> You can also use as property value a **Boolean** variable that evaluates to **true** or **false**. To use a variable for the **Editable** property, it must be set as a global page variable and the [InDataSet Attribute](/dynamics365/business-central/dev-itpro/developer/attributes/devenv-indataset-attribute) must be defined on the variable. Also, note that the dynamic Boolean variables and the Booleans set by the InDataSet attribute aren't supported in tables. 

## See Also

[Properties](devenv-properties.md)   
[Page Properties](./devenv-properties.md)  
[InDataSet Property](/dynamics365/business-central/dev-itpro/developer/attributes/devenv-indataset-attribute)