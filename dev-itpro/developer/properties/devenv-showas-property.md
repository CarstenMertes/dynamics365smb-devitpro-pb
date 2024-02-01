---
title: "ShowAs Property"
description: "Specifies how an action group should be rendered"
ms.author: solsen
ms.custom: na
ms.date: 12/08/2022
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# ShowAs Property
> **Version**: _Available or changed with runtime version 10.0._

Specifies how an action group should be rendered

## Applies to
-   Page Action Group

## Property Value

|Value|Available or changed with|Description|
|-----------|-----------|---------------------------------------|
|**Standard**|runtime version 1.0|Specifies that an action group should be rendered as a standard group.|
|**SplitButton**|runtime version 1.0|Specifies that an action group should be rendered as a split button.|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)


## Syntax

```al
ShowAs = SplitButton; 
```

## Remarks

By specifying that the group should be rendered as **SplitButton**, the group is rendered as a combination of a button and a menu. This type of control gives you a fast one-click access to the first action, which is set to [Visible](devenv-visible-property.md) and to [Enabled](devenv-enabled-property.md) in a menu via the left button part and access to other related actions via the right dropdown part. 

> [!NOTE]  
> Re-ordering the actions in a split button group from a page extension or page customization can change the action used for the split button.

Be aware of the following design guidance:

- Split buttons aren't supported in context menus. When the feature key **ModernActionBar** is turned off, then it isn't supported if the `ShowAs` property is set to `SplitButton` on a promoted action category group.
- Mobile clients don't support split buttons and if the `ShowAs` property is set to `SplitButton`, it will be ignored.
- Any tooltip, caption, or image property set on a group, isn't rendered, if the group is defined as a split button. It's still a best practice to set these properties, because they're used, if the group is rendered as a regular group, for example, on mobile clients.
- A split button can be nested inside another split button.
- For personalization from the UI, it's possible to drop an action into a split button and the action will then become the primary action, if the action is enabled and visible. During personalization it's also possible to reorder the child actions, which will dynamically update the primary action as necessary.


## Example

```AL
group(MyGroup)
{
    ShowAs = SplitButton;
    
    action(MyAction)
    {
    }   
    ...

```

The group `MyGroup` will be rendered as split button, which gives you a one-click access to the action `MyAction`.

## Example 2

The following example illustrates split button behavior if you use a promoted action category with the `ShowAs` property.

```al
...
area(Promoted)
        {
            // Not rendered as a split button when the feature flag is OFF
            group(Category_New) // This is a promoted action category
            {
                Caption = 'New';
                ShowAs = SplitButton;

                actionref(TestAction1_Promoted; TestAction1)
                {
                }

                actionref(TestAction2_Promoted; TestAction2)
                {
                }
            }

            // Rendered as a split button (whether feature flag is ON or OFF)
            group(Test)
            {
                ShowAs = SplitButton;

                actionref(TestAction1_Promoted2; TestAction1)
                {
                }

                actionref(TestAction2_Promoted2; TestAction2)
                {
                }
            }
        }
```


## See Also

[Getting Started with AL](../devenv-get-started.md)  
[Developing Extensions](../devenv-dev-overview.md)  
