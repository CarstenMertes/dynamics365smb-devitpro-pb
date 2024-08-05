---
title: "ShowFilter Property"
ms.date: 10/01/2020
ms.reviewer: na
ms.suite: na
ms.topic: article
ms.assetid: 09cc7138-fbdf-45fe-9cef-3d2e0c95311b
caps.latest.revision: 7
author: SusanneWindfeldPedersen
---

# ShowFilter Property

Sets whether the filter pane is shown on a page by default.  
  
## Applies to  

- Pages  
  
## Property Values  

**True** to show the filter pane; otherwise, **false**. The default value is **true**.

## Syntax

```AL
ShowFilter = false;
``` 
  
## Remarks  

Using customization, a user can override the ShowFilter property setting to show or hide the filter except when the page is displayed in a part of another page, such as a FastTab or FactBox. When the page is displayed in a page part, the ShowFilter property permanently hides or shows the filter pane.

## See Also
[Properties](devenv-properties.md)