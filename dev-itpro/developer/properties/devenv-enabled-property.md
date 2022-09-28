---
title: "Enabled Property"
description: "Sets a value that indicates whether a field or key is enabled or disabled, or whether a control can respond to user-generated events."
ms.author: solsen
ms.custom: na
ms.date: 08/04/2022
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Enabled Property
> **Version**: _Available or changed with runtime version 1.0._

Sets a value that indicates whether a field or key is enabled or disabled, or whether a control can respond to user-generated events.

## Applies to
-   Table Field
-   Table Key
-   Page Label
-   Page Field
-   Page Group
-   Page Part
-   Page System Part
-   Page Chart Part
-   Page Action
-   Page Action Group
-   Page Custom Action
-   Profile

[//]: # (IMPORTANT: END>DO_NOT_EDIT)


> [!NOTE]
> For information about the **Enabled property** for Profiles, see [Enabled (Profile) Property](devenv-enabled-profile-property.md).

## Property Value  
 **True** on pages if the field, key, or control is enabled; otherwise, **false** on pages. The default is **true** on pages and profiles.  

## Syntax

```AL
Enabled = false;
```

## Remarks

For keys, this property determines whether any index (normal or SIFT) defined in the key is created in the database. If you are not using the key or if you rarely use the key, you may want to mark it as disabled for performance reasons. When you want to use the key you can change this setting.  

For fields, this property determines whether you can store data in the field. If the field is unused, disable it to conserve database space. In an XMLPort, a disabled field is read from the external file on import, but it is not inserted in the database.  

For controls, the Enabled setting for the container that contains this control overrides what is entered here.  

On pages, you use the **Enabled** property for group, part, field, and action controls. You can enable or disable the control either statically by setting the property to **true** or **false**, or dynamically by using a Boolean variable or a Boolean field on the page. The Boolean field on the page can be either a true/false Boolean or a Boolean expression, such as “Credit Limit > Sales YTD”.  

> [!NOTE]  
> You can also use as property value a **Boolean** variable that evaluates to **true** or **false**. To use a variable for the **Enabled** property, it must be set as a global page variable and the [InDataSet Property](/dynamics365/business-central/dev-itpro/developer/attributes/devenv-indataset-attribute) must be defined on the variable.

## See Also

[Table Properties](devenv-table-properties.md)  
[Properties](devenv-properties.md)  
[InDataSet Property](/dynamics365/business-central/dev-itpro/developer/attributes/devenv-indataset-attribute)