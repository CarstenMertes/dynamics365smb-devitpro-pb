---
title: "OnPreDataItem Trigger"
description: "OnPreDataItem trigger in AL for Business Central."
ms.date: 04/01/2021
ms.topic: reference
author: SusanneWindfeldPedersen
---

# OnPreDataItem Trigger

Runs before a data item is processed.  

## Syntax  

```AL
trigger OnPreDataItem() 
begin
    ...
end;
```

## Applies to

- Data items  

## Remarks  

This trigger is run before a data item is processed, but after the associated variable is initialized and table views and filters are set.  

You can use this trigger to add additional filtering beyond what is established by the [DataItemLink Property (Reports)](../properties/devenv-dataitemlink-reports-property.md) or [DataItemTableView Property](../properties/devenv-dataitemtableview-property.md). For example, use this trigger if you need to filter an indented data item based on the result of a calculation. Use the [SetRange Record](../methods-auto/record/record-setrange-method.md) or [SetFilter Record](../methods-auto/record/record-setfilter-method.md)  to add extra delimiters.  

## See Also  

[DataItemLink Property (Reports)](../properties/devenv-dataitemlink-reports-property.md)   
[DataItemTableView Property](../properties/devenv-dataitemtableview-property.md)   
[SetRange Method Record](../methods-auto/record/record-setrange-method.md)   
[SetFilter Method Record](../methods-auto/record/record-setfilter-method.md)