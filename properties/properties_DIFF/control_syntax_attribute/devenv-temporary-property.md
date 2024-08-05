---
title: "Temporary Property"
ms.date: 10/01/2020
ms.suite: na
ms.topic: article
author: SusanneWindfeldPedersen
---

# Temporary Property

Sets whether a temporary table is created.  
  
## Applies to  

- Record variables  
  
## Syntax

```AL
var
    TempInvoicePostBuffer: Record "Invoice Post. Buffer" temporary;
```

## Remarks

Changes made to a temporary table are not stored to a database.  
  
## See Also  

[Properties](devenv-properties.md)   
[UseTemporary Property (Report)](devenv-usetemporary-report-property.md)   
[UseTemporary Property (XMLPort)](devenv-usetemporary-xmlport-property.md)    
[Temporary Tables](../devenv-temporary-tables.md)  