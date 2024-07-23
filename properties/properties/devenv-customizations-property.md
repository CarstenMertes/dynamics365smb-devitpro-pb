---
title: "Customizations Property"
author: SusanneWindfeldPedersen
ms.date: 10/01/2020
ms.suite: na
ms.topic: article
ms.author: solsen
---

# Customizations Property

Specifies the list of page customizations associated with this profile.
  
## Applies to  
  
- Profile object  

## Property Value

Comma-separated list of page customization object names.

## Syntax

```AL
Customizations = SimpleCustomization, "My Customization";
```

## Remarks

Page customizations allow you to add changes to a page's layout and actions. You can apply several customizations to a same RoleCenter and use a single customization for different RoleCenters. For more information about creating page customizations, see [Page Customization Object](../devenv-page-customization-object.md).

Page customizations only apply to the RoleCenter they are specified for. In order to see them, in [!INCLUDE[prodlong](../includes/prodlong.md)] under **My Settings**, **Role Center** change to the specific RoleCenter for which a page customization is defined.

## See Also  

[Profile Object](../devenv-profile-object.md)  
[Page Customization Object](../devenv-page-customization-object.md)