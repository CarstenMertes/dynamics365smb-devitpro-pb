---
title: "ChartPartID Property"
ms.date: 10/01/2020
ms.suite: na
ms.topic: article
ms.assetid: 277abf60-998d-4196-b745-ffdcee0b568b
caps.latest.revision: 10
author: SusanneWindfeldPedersen
---

# ChartPartID Property

Sets the ID of the chart to add to the page.  
  
## Applies to  
  
- Part control on a page  
  
<!-- 
> [!IMPORTANT]  
>  This property is not supported by [!INCLUDE[nav_web](../includes/nav_web_md.md)]. When the page displays in [!INCLUDE[nav_web](../includes/nav_web_md.md)], the property is ignored and the chart does not appear.  
--> 

## Syntax
```AL
page 50100 MyPage
{
    layout
    {
        area(Factboxes)
        {
            chartpart(ChartName; ChartPartID)
            {
       
            }

        }
    }
```

## Remarks  

To set this property, you need to first set the value of the [PartType Property](devenv-parttype-property.md) to **Chart**. The ChartPartID property creates a link to the selected chart in the Chart table.  
  
## See Also  

[PartType Property](devenv-parttype-property.md)   
[PagePartID Property](devenv-pagepartid-property.md)   
[SystemPartID Property](devenv-systempartid-property.md)