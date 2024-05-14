---
title: "MaximumDocumentCount Property"
description: Explains the MaximumDocumentCount property on reports in Business Central
ms.date: 10/01/2020
ms.suite: na
ms.topic: article
author: jswymer
---

# MaximumDocumentCount Property

Sets the maximum document count when generating a report by using `WordMergerDataItem`.
  
## Applies To  

- Reports

## Property Value

An integer
 
## Syntax

```AL
MaximumDocumentCount = 100;
```

## Remarks

At runtime, this property will override the hard limit that is set by the **Default Max Documents** (ReportDefaultMaxDocuments) setting for [!INCLUDE[server](../includes/server.md)] instance. The [!INCLUDE[server](../includes/server.md)] instance also includes the **Max Documents (hard limit)** (ReportMaxDocuments) setting, which this property won't override.

## See Also  

[Report Properties](devenv-report-properties.md)  
[Report Object](../devenv-report-object.md)  
[Configuring Business Central Server - Reports](../../administration/configure-server-instance.md#Reports)  
[Operational Limits for Business Central Online - Reports](../../administration/operational-limits-online.md#Reports)  