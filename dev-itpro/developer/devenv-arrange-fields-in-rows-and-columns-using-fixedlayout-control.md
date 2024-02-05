---
title: Arranging Fields in Rows and Columns Using a fixed Control
description: A fixed control is used to arrange page fields in rows and columns, similar to a matrix-like format, which is typically used to display statistical data.
ms.custom: bap-template
ms.date: 02/06/2023
ms.reviewer: na

ms.topic: conceptual
author: jswymer
ms.author: jswymer
---

# Arranging fields in rows and columns using the fixed control

By default, fields on a FastTab are arranged automatically in two columns based on the number of fields. For more information on how the fields are placed on a page, see [Field Arrangement on a Fasttab](devenv-arranging-fields-on-fasttab.md). To arrange fields manually, you can either use a Grid control to design the page to look like a grid-like format, or a fixed control to design the page to look like a matrix-like format. To understand the differences between the two controls to help you determine which control to use, see [Comparing Grid and Fixed controls](devenv-arranging-fields-using-grid-and-fixed-controls.md).

> [!IMPORTANT]  
> Fields in a fixed layout are not editable even if the **Editable** property is set to **true**. However, if the field drills down to a page where the field source is defined, then you can modify the field. For more information, see [Editable Property](properties/devenv-editable-property.md).

## How fixed control works

Use the fixed control to arrange page fields in rows and columns to form a matrix-like layout. The difference is that the fixed control contains a specific number of fields, and a matrix can contain an unspecified number of fields. A Fixed group control is typically used to display statistical data. The following illustration shows an example of a page that uses a fixed control to show sales totals for different time periods.   

![Fixed control illustration on web client.](media/BusWebClientFixedLayout.PNG "BusinessCentralFixedControl") 

You can also use a fixed control to display information in the details section of a Worksheet page. If you're using the [!INCLUDE[demolong](includes/demolong_md.md)], then you can see examples of these uses in page 151, Customer Statistics, and page 40, Item Journal.
  
## Adding fields

You can add fields directly in the fixed control. However, when you add fields directly in the fixed control, all the fields will display in an equal size and the larger fields will get compressed. The following illustration shows the resulting field layout on a page.  
  
![Fixed control illustration of a single row of fields.](media/BusRTCFixedLayoutSingle.png "BusinessCentralFixedControlSingle") 

## Grouping fields in a fixed control

By placing the fields in a fixed control throughout a group control, you can define separate rows and columns to create a matrix-like arrangement. The group control caption appears as the column header, and the field control captions appear as the row headers. If you add two more group controls that contain fields, then the layout on the page will display like a table format.

### Example

The following AL code uses **fixed** control to display four fields on a page inside the group called Fixed Layout.

```AL
page 50114 "Fixed Control Example"
{    
    layout
    {
        area(content)
        {
            group("Fixed Layout")
            {
                fixed(DefiningFixedControl)
                {
                    group("Group Caption")
                    {
                        field("Field 1"; "Field 1")
                        {
                            ApplicationArea = All;
                        }
                        field("Field 2"; "Field 2")
                        {
                            ApplicationArea = All;
                        }
                        field("Field 3"; "Field 3")
                        {
                            ApplicationArea = All;
                        }
                        field("Field 4"; "Field 4")
                        {
                           ApplicationArea = All;
                        }                   
                    }
                }
            }
        }
    }
   var
        "Field 1": Integer;
        "Field 2": Integer;
        "Field 3": Integer;
        "Field 4": Integer; 
}
```

The following illustration shows the resulting field layout on a page.  
  
![Fixed control illustration showing 4 fields.](media/BusRTCFixedLayoutGroup.png "Showing4FieldsFixedControl")  
  
The group control caption appears as the column header, and the field control captions appear as the row headers. If you add two more group controls that contain fields, then the layout on the page will resemble the following illustration.  

> [!NOTE]  
> Only the captions of fields in the first column define the row headings. Therefore, only the field captions for the first group control appear. The field captions in other group controls are ignored.  
  
![Fixed control in multiple groups.](media/BusRTCFixedLayoutMultipleGroups.png "FixedControlMultipleGroups") 

## Column header alignment

Starting in Business Central 2023 release wave 1 (v22.0), column headers are automatically right-aligned. Similar to all other cases in Business Central, you can't explicitly specify field value alignment. Column headers are left-aligned in earlier releases.

## Using multiple fixed controls

You can also set up more than one fixed control in a group control. The page area will then divide the fields into two columns that contain the separate fixed fields. For example, the following illustration shows the page layout if you have four fixed controls.  

![Multiple Fixed controls in a single group.](media/BusRTCFixedLayoutMultiple.png "FixedControlMultiple") 

> [!NOTE]  
> The fields in the fixed controls in the illustration are not in a group control. If they were in a group control, then they would follow the same principle as described in the previous section about how to group fields. 

> [!IMPORTANT]  
> In previous versions, having a fixed control directly under a content area was supported. However, in [!INCLUDE[d365_bus_central_md](includes/d365_bus_central_md.md)], you must make sure that the fixed control is nested in a Group control. For more information, see [Supported Structure for Using the Grid and Fixed Controls](devenv-arranging-fields-using-grid-and-fixed-controls.md#supported-structure-for-using-the-grid-and-fixed-controls).

## See Also

[Field Arrangement on a FastTab](devenv-arranging-fields-on-fasttab.md)  
[Pages Overview](devenv-pages-overview.md)  
[Arranging Fields Using Grid and Fixed Controls](devenv-arranging-fields-using-grid-and-fixed-controls.md)  
[Arranging Fields in Rows and Columns Using the GridLayout Control](devenv-arrange-fields-in-rows-and-columns-using-gridlayout-control.md)  