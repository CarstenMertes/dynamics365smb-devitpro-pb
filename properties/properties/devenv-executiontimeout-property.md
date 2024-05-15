---
title: "ExecutionTimeout Property"
description: Explains the ExecutionTimeout property on reports in Business Central
ms.date: 10/01/2020
ms.suite: na
ms.topic: article
author: jswymer
---

# ExecutionTimeout Property

Sets the maximum time the report will run after which it is automatically terminated. 
  
## Applies To  

- Reports

## Property Value

A string in the format `hh:mm:ss`.

## Syntax

```AL
ExecutionTimeout := `10:05:55`;
```

## Remarks

At runtime, this property will override the limit that is set by the **Default Max Rendering Timeout** (ReportDefaultTimeout) setting for [!INCLUDE[server](../includes/server.md)] instance. The [!INCLUDE[server](../includes/server.md)] instance also includes the **Max Rendering Timeout (hard limit)** (ReportTimeout) setting, which this property won't override.

## See Also  

[Report Properties](devenv-report-properties.md)  
[Report Object](../devenv-report-object.md)  
[Configuring Business Central Server - Reports](../../administration/configure-server-instance.md#Reports)  
[Operational Limits for Business Central Online - Reports](../../administration/operational-limits-online.md#Reports)  