---
title: "CustomActionType property"
description: "Sets the type of the custom action."
ms.author: solsen
ms.date: 08/26/2024
ms.topic: reference
author: SusanneWindfeldPedersen
ms.reviewer: solsen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# CustomActionType Property
> **Version**: _Available or changed with runtime version 10.0._

Sets the type of the custom action.

## Applies to
-   Page Custom Action

## Property value

|Value|Available or changed with|Description|
|-----------|-----------|---------------------------------------|
|**Flow**|runtime version 10.0|An action that can trigger a Power Automate Flow.|
|**FlowTemplate**|runtime version 11.0|An action that can trigger a Power Automate template editor to create a new Flow from a specific template.|
|**FlowTemplateGallery**|runtime version 11.0|An action that can trigger a Power Automate template gallery to create a new Flow from a selection of templates.|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

To learn more about Power Automate flows with Business Central, see [Power Automate Integration Overview](../../powerplatform/power-automate-overview.md).

## Examples

The following examples illustrate the syntax of the three custom action types. The first example extends the **Customer Card** page with a promoted action that runs a Power Automate flow that has the flow ID `00001111-aaaa-2222-bbbb-3333cccc4444`.

```al
pageextension 50100 CustomerCardExt extends "Customer Card"
{
    actions
    {
        
        addlast(processing)
        {
            customaction(MyFlowAction)
            {
                ApplicationArea = All;
                CustomActionType = Flow;
                FlowId = '00001111-aaaa-2222-bbbb-3333cccc4444';
                FlowEnvironmentId = 'Default-44445555-eeee-6666-ffff-7777aaaa8888';
            }
        }
        addfirst(Promoted)
        {
            actionref(MyFlowPromoted; MyFlowAction)
            {
            }
        }

    }
}
```

This next code example extends the **Customer Card** page with a promoted action that triggers opening a specific Power Automate template wizard directly. The `FlowTemplateId` property specifies, which template wizard to open.

```al
pageextension 50100 CustomerCardExt extends "Customer Card"
{
    actions
    {
        
        addlast(processing)
        {
            customaction(MyFlowAction)
            {
                ApplicationArea = All;
                CustomActionType = FlowTemplate;
                FlowTemplateId = '00001111-aaaa-2222-bbbb-3333cccc4444';
                FlowCaption = 'Create a Power Automate flow using a template';
            }
        }
        addfirst(Promoted)
        {
            actionref(MyFlowPromoted; MyFlowAction)
            {
            }
        }

    }
}
```

This third code example likewise extends the **Customer Card** page with a promoted action, this time it triggers opening the Power Automate template gallery wizard for the user to create a new Flow from a selection of templates. The `FlowTemplateCategoryName` property sets the category used to filter the list of Power Automate templates shown in the template gallery.

```al
pageextension 50100 CustomerCardExt extends "Customer Card"
{
    actions
    {
        
        addlast(processing)
        {
            customaction(MyFlowAction)
            {
                ApplicationArea = All;
                CustomActionType = FlowTemplateGallery;
                FlowTemplateCategoryName = 'd365bc_approval_generalJournal';
                FlowCaption = 'Select and create a Power Automate flow using a template';
            }
        }
        addfirst(Promoted)
        {
            actionref(MyFlowPromoted; MyFlowAction)
            {
            }
        }

    }
}
```

## Related information  
[Getting Started with AL](../devenv-get-started.md)  
[Developing Extensions](../devenv-dev-overview.md)  