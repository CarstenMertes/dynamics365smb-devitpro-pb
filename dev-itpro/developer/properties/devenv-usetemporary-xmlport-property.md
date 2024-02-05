---
title: "UseTemporary Property (XMLport)"
author: solsen
ms.custom: na
ms.date: 04/01/2021
ms.reviewer: na
ms.topic: reference
ms.assetid: 729f3649-f7c8-498d-8c16-961771f192a0
ms.author: jswymer
---
 
# UseTemporary Property (XMLport)
> **Version**: _Available from runtime version 1.0._

Sets whether a temporary table is created to store the records imported using the XmlPort.

## Applies to  

- XMLport table elements


## Syntax

```AL
UseTemporary = true;
```

## Remarks

If the data that you are importing has a different structure than the table in [!INCLUDE[d365fin_long_md](../includes/d365fin_long_md.md)] that you want to insert it into, you could import the data into a temporary table. The temporary table holds the data in cache without writing it to the database. You can then modify the data before inserting it into the database.

## See Also  

[Properties](devenv-properties.md)   
[XMLPort Object](../devenv-xmlport-object.md)   
[UseTemporary Property (Report)](devenv-usetemporary-report-property.md)  
[Temporary Tables](../devenv-temporary-tables.md)

