---
title: "OnBeforeOpen Trigger"
description: "OnBeforeOpen trigger in AL for Business Central."
ms.date: 04/01/2021
ms.topic: reference
author: SusanneWindfeldPedersen
---

# OnBeforeOpen Trigger

Runs before a query is run and the dataset is generated.  

## Syntax  

```AL
trigger OnBeforeOpen()
begin
    ...
end;
```  

## Remarks

The AL code of a query object includes the OnBeforeOpen trigger that you can use to change the data that will be included in the resulting dataset. For example, you can use the OnBeforeOpen trigger to apply filters to a column.  

The OnBeforeOpen trigger only supports local variables; global variables are not supported.  

> [!NOTE]  
> A query cannot be run from the OnBeforeOpen trigger. You cannot call methods from the triggers that run the query, such as Open, SaveAsXml, Read, or Close methods.  

## Example

The following code applies a filter on the Quantity column of the query by calling the SetFilter on the OnBeforeOpen trigger of the query object.  

```AL
currQuery.SetFilter(Quantity, '>50');  
```  

## See Also

[Triggers](devenv-triggers.md)  
