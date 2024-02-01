---
title: "SharedLayout Property"
description: "Specifies whether the view has the same layout as the default view 'All'."
ms.author: solsen
ms.custom: na
ms.date: 03/09/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# SharedLayout Property
> **Version**: _Available or changed with runtime version 4.0._

Specifies whether the view has the same layout as the default view 'All'.
When set to true, user personalization on the page is also applied when the view is selected.
When set to false, the view defines its own layout and is not affected by user personalization.

## Applies to
-   Page View

[//]: # (IMPORTANT: END>DO_NOT_EDIT)


## Property Values  

When set to **true**, user personalization on the page is also applied when the view is selected. When set to **false**, the view defines its own layout and is not affected by user personalization.


## Syntax

```AL
SharedLayout = false;
``` 
  
## Remarks  

### Shared layout view

A view with `SharedLayout = true` follows the design of the **All** page and any user personalization made on **All** or any of the views marked with `SharedLayout` are applied on the view. They all share the same layout. This is a basic experience in the case where defining a specific layout for the view is not important. The view is then filter only. 

#### Example 1

```AL
view(SharedLayoutView) 

{ 
    // This view only define filters, but no specific layout. 
    // User personalization are applied on this view. 
    Caption = 'View With Shared Layout'; 
    Filters = where("Balance Due (LCY)" = filter(> 10000)); 
} 
```

### Unique layout view

A view with unique layout `SharedLayout = false` defines its own layout and is independent from all other views. Any changes coded in the layout sections are applied in the view. User personalization made on the page are not applied on that view.

### Example 2

```AL
view(UniqueView)
{
    Caption = 'View With Unique Layout';
    Filters = where("Balance Due (LCY)" = filter(> 10000));
    // By settings this property to false, the view gets its own independent layout.
    // User personalization are not applied on this view.
    // Instead, the layout defined below is applied.
    SharedLayout = false;
    
    layout
    {
        movefirst(Control1; "Balance Due (LCY)")
    }
}
```

> [!NOTE]  
> `SharedLayout = false` must be specified in order to use a custom layout on the view (the layout section). A compiler error is reported otherwise.

## See Also

[Properties](devenv-properties.md)  
[Views](../devenv-views.md)