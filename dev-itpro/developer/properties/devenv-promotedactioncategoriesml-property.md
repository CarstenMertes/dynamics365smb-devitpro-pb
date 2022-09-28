---
title: "PromotedActionCategoriesML Property"
description: "Sets the caption of the group that you are promoting the action to."
ms.author: solsen
ms.custom: na
ms.date: 06/15/2022
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# PromotedActionCategoriesML Property
> **Version**: _Available or changed with runtime version 1.0._

Sets the caption of the group that you are promoting the action to.

## Applies to
-   Page

[//]: # (IMPORTANT: END>DO_NOT_EDIT)


## Syntax

```AL
PromotedActionCategoriesML = ENU='New,Process,Report,Bank,Application', ESP='Nuevo, Procesar, Reportar, Banco, Aplicación';
```
 
## Remarks  

> [!NOTE]  
> With [!INCLUDE [prod_short](../includes/prod_short.md)] 2022 release wave 2, the way that you promote actions on pages or page extensions has changed. Promoting actions is defined in a specific section of the page definition and contains a reference to the action. For more information, see [Promoted Actions](../devenv-promoted-actions.md).

The PromotedActionCategoriesML property is multilanguage enabled, so it can contain a list of text strings in different languages. The string that is used is selected according to the user's language settings. For more information, see [Multilanguage Development](../devenv-work-with-translation-files.md).

Promoted actions appear in the action bar on a page. You promote an action by setting the [Promoted Property](devenv-promoted-property.md) to **true**. You use the  [PromotedCategory Property](devenv-promotedcategory-property.md) to set the category of an action, which allows you to group similar actions under a common caption. You can choose between 20 categories: New, Process, Report, and Category4 through Category20.

By default, the category names are used as the captions in the ribbon. You use this property to customize these captions. The new caption names must me expressed as a string list, where the first three places correspond to the captions of the New, Process and Report categories, respectively, the fourth place to Category4's caption, the fifth to Category5's and so on.
<!-- For information about changing the captions, see [How to: Define Promoted Action Categories Captions for the Ribbon](How-to--Define-Promoted-Action-Categories-Captions-for-the-Ribbon.md).  -->

> [!NOTE]  
> Any empty spaces in the string of promoted action categories are removed. This means that `PromotedActionCategories = 'New caption,,,Category4 caption';` is interpreted as `PromotedActionCategories = 'New caption,Category4 caption';`. To maintain the sequence, you must fill in any empty spaces by, for example, using `Category4`, `Category5` etc.
  
## See Also  

[Properties](devenv-properties.md)  
[Promoted Property](devenv-promoted-property.md)  
[PromotedActionCategories Property](devenv-promotedactioncategories-property.md)  
[PromotedCategory Property](devenv-promotedcategory-property.md)  
[Actions Overview](../devenv-actions-overview.md)  
