---
title: "LinksAllowed property"
description: "Sets whether links are allowed."
ms.author: solsen
ms.date: 02/18/2025
ms.topic: reference
author: SusanneWindfeldPedersen
ms.reviewer: solsen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# LinksAllowed Property
> **Version**: _Available or changed with runtime version 1.0._

Sets whether links are allowed.

## Applies to
-   Request Page
-   Page

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Property Value

**True** if links are allowed; otherwise, **false**. The default value is **true**.  

## Syntax

```AL
LinksAllowed = false;
```  

## Remarks

If LinksAllowed is set to **true**, then you can add links or notes to a page. The links can be a links to web sites, files stored on the local computer or on a remote computer, or links to pages.  
  
On a page, the links and notes are displayed in FactBoxes. If LinksAllowed is set to **true**, then the **Actions** menu has a **Notes** item and a **Links** item. You use these to create and modify notes and links.  
  
## Related information

[Properties](devenv-properties.md)