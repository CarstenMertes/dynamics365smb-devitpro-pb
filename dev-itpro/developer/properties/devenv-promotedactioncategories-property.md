---
title: "PromotedActionCategories Property"
description: "Sets a category for a promoted action."
ms.author: solsen
ms.custom: na
ms.date: 07/01/2022
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# PromotedActionCategories Property
> **Version**: _Available or changed with runtime version 1.0._

Sets a category for a promoted action.

## Applies to
-   Page

[//]: # (IMPORTANT: END>DO_NOT_EDIT)


## Parameters

*Locked*  
&emsp;Type: [Boolean](../methods-auto/boolean/boolean-data-type.md)  
If `true` the PromotedActionCategories is locked and should not be translated.  

*Comment*  
&emsp;Type: [Text](../methods-auto/text/text-data-type.md)  
Descriptive text for the PromotedActionCategories, for example, with regards to translation.

*MaxLength*  
&emsp;Type: [Integer](../methods-auto/integer/integer-data-type.md)  
Sets the maximum length of the specific PromotedActionCategories property value.

## Syntax

```AL
PromotedActionCategories = 'New caption,Process caption,Report caption,Category4 caption';
```

Or, with parameters:

```AL
PromotedActionCategories = 'New caption,Process caption,Report caption,Category4 caption', Locked = true, Comment = 'Keep like this, do not translate.', MaxLength = 100;
```

## Remarks  

> [!NOTE]  
> With [!INCLUDE [prod_short](../includes/prod_short.md)] 2022 release wave 2, the way that you promote actions on pages or page extensions has changed. Promoting actions is defined in a specific section of the page definition and contains a reference to the action. For more information, see [Promoted Actions](../devenv-promoted-actions.md).

Promoted actions appear in the action bar on a page. You promote an action by setting the [Promoted Property](devenv-promoted-property.md) to **true**. You use the  [PromotedCategory Property](devenv-promotedcategory-property.md) to set the category of an action, which allows you to group similar actions under a common caption. You can choose between 20 categories: New, Process, Report, and Category4 through Category20.

By default, the category names are used as the captions in the ribbon. You use this property to customize these captions. The new caption names must be expressed as a string list, where the first three places correspond to the captions of the New, Process and Report categories, respectively, the fourth place to Category4's caption, the fifth to Category5's and so on.

> [!NOTE]  
> Any empty spaces in the string of promoted action categories are removed. This means that `PromotedActionCategories = 'New caption,,,Category4 caption';` is interpreted as `PromotedActionCategories = 'New caption,Category4 caption';`. To maintain the sequence, you must fill in any empty spaces by, for example, using `Category4`, `Category5` etc.

## See Also  

[Properties](devenv-properties.md)  
[Promoted Property](devenv-promoted-property.md)  
[PromotedActionCategoriesML Property](devenv-promotedactioncategoriesml-property.md)  
[PromotedCategory Property](devenv-promotedcategory-property.md)  
[Actions Overview](../devenv-actions-overview.md)  
