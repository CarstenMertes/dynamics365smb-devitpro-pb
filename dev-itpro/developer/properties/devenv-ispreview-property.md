---
title: "IsPreview Property"
description: "Specifies if the page is available as part of a preview release."
ms.author: solsen
ms.custom: na
ms.date: 10/25/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# IsPreview Property
> **Version**: _Available or changed with runtime version 12.1._

Specifies if the page is available as part of a preview release.

## Applies to
-   Page

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

The `IsPreview` property displays a note in the UI that the page or feature is currently in preview and is subject to change. The default value is `false`. This property is used when the `PageType` property is set to `PromptDialog`. For more information, see [The PromptDialog object](../devenv-page-type-promptdialog.md). 

Setting `IsPreview` to `true` has no further impact across Business Central. It has no relation to the private or public preview programs for any Microsoft products, nor is it exclusive to sandbox environments.

## See Also

[Getting Started with AL](../devenv-get-started.md)  
[Developing Extensions](../devenv-dev-overview.md)  
[The PromptDialog object](../devenv-page-type-promptdialog.md)  
[PromptMode property](devenv-promptmode-property.md)  
[PageType property](devenv-pagetype-property.md)