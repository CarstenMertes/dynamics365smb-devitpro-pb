---
title: Use Designer
description: Description of how Designer works and is integrated with the AL development experience.
author: jswymer
ms.author: jswymer
ms.reviewer: jswymer
ms.topic: conceptual
ms.date: 01/16/2024
ms.custom: bap-template
ms.collection: get-started
---

# Use Designer

When developing extensions in the AL development environment, you have a wide range of possibilities. Designer in [!INCLUDE[d365fin_long_md](includes/d365fin_long_md.md)] complements the development experience in Visual Studio Code. It provides an easy and convenient way to make immediate changes to your design by dragging and dropping the components on the page.  

> [!IMPORTANT]  
> Currently, Designer is only available from a [!INCLUDE[d365fin_long_md](includes/d365fin_long_md.md)] sandbox.<br> Every time you start designing, you're effectively creating a new extension. Your changes are immediately visible to other users in the sandbox environment.<br> Designer cannot be used by multiple users at the same time in sandboxes.  

> [!NOTE]  
> Extensions created Use Designer are removed when the sandbox environment is updated or relocated within our service. Thus, you should not rely on using the sandbox environment as a source control for these Designer extensions. Remember to frequently download and backup the Designer extension source. For more information, see [Production and Sandbox Environments](../administration/environment-types.md).

## Designer capabilities

Here's a quick overview of capabilities in **Designer**: 

|Features      |Applies to    | 
|--------------|--------------|
|Add components    |fields, columns, parts, actions in navigation bar              | 
|Move components   |fields, columns, cues, parts, actions, and action groups |
|Remove components |fields, columns, cues, parts, actions, and action groups |
|Hide and unhide components|parts|
|Change field importance, like showing in collapsed FastTab header or under **Show More** |fields|
|Exclude field from Quick Entry|fields, columns| 
|Set freeze pane and clear freeze pane |columns|
|Adjust column width |columns |
|Edit caption        |FastTabs, cards, FactBoxes   |
|Save extension/download code |general           |
|Preview design               |general           |

[!INCLUDE[Personalization of the controls](../includes/designer_experience_of_the_controls_note.md)]

## Important points to note

- Every time you start designing, you're effectively creating a new extension. Your changes are immediately visible to other users in the sandbox environment.
- The changes you make in Designer will apply to **all** users.
- You can't remove specific fields that are bound to a page and a field must belong to an underlying table.
- You can only add fields, columns, or tiles to its applicable view from list, tall tiles, and wide tiles views. Some components can't be moved using drag-and-drop and are restricted to the view that they are in.
- You can only add fields/columns, from a predefined list, which is based on the source table. You can't create new ones.
- In the client, users can change many of these settings for their workspace by using personalization. For more information, see [Personalizing Your Workspace](/dynamics365/business-central/ui-personalization-user).  

## Start and stop designing

In the [!INCLUDE[prod_short](includes/prod_short.md)] client, you start Designer by choosing ![Settings icon.](media/settings_icon_small.png) icon and then **Design** in the top-right corner of any page and start designing using drag-and-drop components. In Visual Studio Code, you can start Designer by using the <kbd>F6</kbd> shortcut key, which launches a browser that opens the [!INCLUDE[prod_short](includes/prod_short.md)] client in Designer.

After you're done with the changes, choose **Stop Designing**. You can name the extension and download code to save it for the tenant. Once you're done, the extension is automatically installed. If you choose to download the code, the project will be downloaded as a .zip folder<!--, where the `app.json` file has the main extension as a dependency-->. You extract the files and open the folder from Visual Studio Code, where you can deploy it as you would do with any other extension.

If you choose not to download the code at the end, you can still pull the code using the <kbd>Alt</kbd>+<kbd>F6</kbd> shortcut. You can also uninstall the extension from the **Extension Management** page or even download the source from there. You can find **Extension Management** page by choosing the search ![Lightbulb that opens the Tell Me feature.](../media/search_small.png "Tell me what you want to do") icon and typing the page name.


![Work with Designer.](media/designer.gif)

## Drag-and-drop components

In Designer, you design and modify the current page by using drag and drop components. You can display existing table fields, move fields around, remove fields from the page, hide and move actions, and much more.

## Work with fields

To add a field or column to a page, in the banner, choose **Field**. A pane to the right appears that lets you add fields. Here, you can see all the fields that are available for the specific page. The fields displayed are based on the underlying table or tables. The field can have a status of **Placed**, which means that the field already exists on the page. A status of **Ready** means that the field doesn't exists on the page and can be added. To add a field, drag and drop it to the preferred location.

If you want to remove a field or column, select the arrowhead indicator ![arrowhead indicator left.](media/designer_arrow_left.png) or ![arrowhead indicator down](media/designer_arrow_down.png) on the component, and then choose **Remove**.

You can edit the caption of a FastTab (FastTabs divide key information in separate groups and are arranged in columns) by selecting the caption and start writing. A caption should provide a short and clear description. For more information, see [Field Arrangement on FastTabs](devenv-arranging-fields-on-fasttab.md)

## Set the freeze pane

**Set freeze pane** locks one or more columns to the left, even when you scroll horizontally. You can set the freeze pane, by selecting the arrowhead indicator ![arrowhead indicator left.](media/designer_arrow_left.png) or ![arrowhead indicator down](media/designer_arrow_down.png) of the column that you want as the last column of the freeze pane, and then choose **Set Freeze Pane**. If you want to set the freeze pane back to its original designed location, select the arrowhead indicator ![arrowhead indicator left](media/designer_arrow_left.png) or ![arrowhead indicator down](media/designer_arrow_down.png) for the current freeze pane column, and then choose **Clear Freeze Pane**.

## Set the Importance on a field

Fields on non-list type pages, such as card and document type pages, include Designer options for setting the importance. The following table describes the options for setting the importance in Designer and how it corresponds to the [Importance property](properties/devenv-importance-property.md) in the page code.

|Option|Description|Importance property value|
|----|----|---|
|**Show under "Show more"**|Sets the field so that it appears only when the user selects **Show more**. |Additional|
|**Show always**|Sets the field to always display on the page. The field is displayed regardless the user selects **Show more** or **Show less**. The field won't show in the FastTab heading if the FastTab is collapsed.|Standard|
|**Show when collapsed**|Sets the field to always display on the page. The field is displayed regardless the user selects **Show more** or **Show less**. The fields will also display in the header of the FastTab if the FastTab is collapsed.|Promoted|

## Set the Quick Entry on fields

You can use Designer to set the [QuickEntry property](properties/devenv-quickentry-property.md) on a field. The **QuickEntry** property determines whether the field is skipped when users select the <kbd>Enter</kbd> key to navigate through fields on a page. You use Quick Entry to speed up the data entry by keyboard and to focus only on the frequently used fields.

To set the QuickEntry property from Designer, select the field or column heading, and then choose either **Include in Quick Entry** (sets the **QuickEntry** property to `true`) or **Exclude from Quick Entry** (sets the **QuickEntry** property to `false`).  

For more information about QuickEntry property, from a user perspective, see [Accelerating Data Entry Using Quick Entry](/dynamics365/business-central/ui-enter-data#QuickEntry) in the [!INCLUDE[prod_short](includes/prod_short.md)] Application Help.

## Work with the Navigation menu and Navigation bar

Designer lets you add actions that link to pages and reports in the navigation bar using the bookmark icon ![bookmark icon.](media/ui_bookmark_icon.png "bookmark icon action bar") on the target page or report. The bookmark icon is also available in the Tell Me window.

> [!NOTE]
> Bookmarking is only available for pages and reports that are discoverable from Tell Me (search icon on top right). For more information on how to make pages and reports searchable, see [Add pages and reports to Tell me](devenv-al-menusuite-functionality.md).

This feature allows the user to efficiently create multiple links and group together the important or commonly used links for a specific profile in the Role Center navigation bar. For more information about bookmarking, see [Bookmark a Link to a Page or Report on Your Role Center](/dynamics365/business-central/ui-bookmarks) in the [!INCLUDE[prod_short](includes/prod_short.md)] Application Help.

You can also move actions to reorder them in the navigation bar, or move them into groups or subgroups to design the Navigation Menu.

## Hide and show Parts

Designer lets you hide and unhide part controls in a page directly from the client. When you select the **Hide** option on a part, it will be grayed-out and disappear from the page when you quit Designer mode. Similarly, you can select **Show** on a grayed part control to make it visible again to the user. 

The extension generated when the user hides or shows a part overrides the [Visible Property](properties/devenv-visible-property.md) in code. For more information on how the **Visible Property** affects the visibility of a control, see [UI Customization and Visibility of Controls](properties/devenv-visible-property.md#ui-customization-and-visibility-of-controls).

## Work with Actions

Designer lets you make changes to the actions that are defined in the action bar of a page. You can move, remove, hide, and show individual actions or action groups.  

![Designer action bar.](media/designer-action-bar.png "Designer action bar")

> [!NOTE]
> You cannot modify actions that are defined on pages that are shown in parts, such as in FactBoxes or embedded lists. 

> [!TIP]
> In Designer, to run an action as normal, select the action and select <kbd>Ctrl</kbd>+Click.

### Remove, hide, and show actions and groups

Actions and actions groups that are already hidden appear dimmed. To change the state of an action or action group, select it, and then choose one of the following options:

|Option|What it does|
|------|------------
|**Remove**|This option is available for the actions that are shown only in a promoted category. Or actions that are shown in both, promoted category and another action menu.<br /><br /> Choosing **Remove** deletes the action from the selected location so that it no longer appears.<br /><br /> If the action is only shown in the promoted category, it will automatically be shown in the action menu where it's originally defined.<br /><br />You can't remove actions on a Role Center page; you can only hide them.|
|**Hide**|This option is available for actions or action groups that are currently shown only in an action menu (not in a promoted category). Like **Remove**, choosing **Hide** will make the action or action group disappear from the action bar in the client. However, in Designer, the action or action group appears dimmed.|
|**Show**|This option appears if the action or action group has been previously hidden (dimmed). Choosing this option will make the action or action group appear in the action bar.|

### Move actions and action groups

Designer lets you move actions within the action bar. For example, you can:

- Move an action from an action menu to a promoted category.
- Move an action from one promoted category to another.
- Move an action within an action group or to a different action group.  

To move an action or action group, drag and drop it to the wanted location, just like with fields and columns.  

- You can move individual actions into the promoted categories, but you can't change the order of the actions in the category.
- You can't move an action group into a promoted category.
- To move an action or action group into an empty action group, drag the action or action group to the target group and drop it in the **Drop an action here** box.
- On Role Center pages, you can't move actions among the different areas that are defined by the `area(creation)`, `area(processing)`, and `area(reporting)` controls.

## Preview design on different display targets

The display type icons let you preview the changes you made on desktop, tablet, and phone clients. This way you can make sure that your design will work on the intended display target(s). You can flip to display tablet and phone designs in portrait and landscape orientation. 

## Control user access to Designer

Accessing Designer is controlled on a user or user group basis by the **EXTEN. MGT. - ADMIN** permission set. If a user is assigned this permission set, then Designer is available for the user in the client. To prohibit a user from Use Designer, just remove the user from the **EXTEND. MGT. - ADMIN** permission set.

> [!NOTE]  
> It's important that the **EXTEN. MGT. - ADMIN** permission set does not have a *company* specified; otherwise the user won't be able to access Designer.

> [!NOTE]
> The **EXTEN. MGT. - ADMIN** permission set was introduced in Business Central 2021 release wave 1 as a replacement for the **D365 EXTENSION MGT** permission set in earlier versions.

## Other things to know

- **Power Automate** item in action bar

  - You can't hide or move the **Automate** item or the **Power Automate** subitem and its actions **Create a flow** or **Manage Flows**.
  - You can move flows included under the **Automate** item, but you can't hide them. Moving the flow makes a copy of the flow to the destination, it won't remove it from the **Automate** item. Your flow in Power Automate isn't duplicated.
    - If the action is moved to the repository area of the action bar (right side of |), a new `action` is created at the drop location.
    - If the action is moved to the promoted area (left side of |) a new `actionref` is created at the drop location. This `actionref` points to a new base action that's appended to the **Actions** menu (`Processing` action area).
   > [!TIP]
   > You can hide the **Automation** item from users, but not Use Designer. Learn more at [Set Up Power Automate Integration](../powerplatform/power-automate-setup.md).

## See also

[Developing Extensions](devenv-dev-overview.md)  
[Get Started with AL](devenv-get-started.md)  
[AL Development Environment](devenv-reference-overview.md)
