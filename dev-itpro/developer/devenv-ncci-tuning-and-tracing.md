---
title: "NCCI Tuning and Tracing"
description: Explains how to tune and trace nonclustered columnstore indexes in Business Central.
ms.custom: na
ms.date: 01/28/2022
ms.reviewer: na
ms.topic: conceptual
author: jswymer
---
# Nonclustered Columnstore Indexes Tuning and Tracing

Nonclustered columnstore (NCCIs) indexes are exposed to SQL Server tracing and tuning tools. For example, the SQL Server profiler can display information about which columnstore indexes are used in the system. This information makes it easy for you to assess the cost of maintaining an NCCI. It allows you to make informed decisions about any adjustments that might be required.  
  
## SIFT keys versus NCCIs

When data is inserted, updated, or deleted in a table, the SIFT keys that are defined and enabled for that table are maintained. Maintaining these SIFT indexes has performance overhead. The size of the performance overhead depends on the number of keys and SumIndexFields that have been defined for each table. So give careful consideration to the number of SIFT keys that you define. Only maintain the SIFT keys that are important for your application.  
  
With an NCCI, only one index structure exists and needs to be maintained. So there's no need to consider which query scenarios should be indexed.

## See Also

[NCCI Overview)](devenv-ncci-overview.md)  
[NCCI and SQL Server](devenv-ncci-and-sql-server.md)  
[NCCI Performance](devenv-ncci-performance.md)  
[Migrating from SIFT to NCCI](devenv-migrating-from-sift-to-ncci.md)  
[SumIndexField Technology \(SIFT\)](devenv-sift-technology.md)  
[FlowFields](devenv-flowfields.md)  