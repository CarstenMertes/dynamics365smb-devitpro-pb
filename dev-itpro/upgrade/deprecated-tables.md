---
title: Deprecated Tables
description: Shows the tables that have been marked as removed in the various versions of Business Central.
ms.custom: na
ms.date: 04/01/2021
ms.reviewer: na
ms.topic: conceptual
author: SusanneWindfeldPedersen
ms.author: solsen
---

# Deprecated Tables

[!INCLUDE [2020_releasewave1](../includes/2020_releasewave1.md)]

Across the different versions of [!INCLUDE[prod_short](../developer/includes/prod_short.md)], a number of tables have been deprecated.  

## Changes in 2020 release wave 1

The following tables have been marked with an `ObsoleteState:Removed`. Code that uses the deprecated table or tables, must be rewritten to use the new table or tables. The deprecated tables are mapped as follows:

|Deprecated Table Name|New Table Name|
|---------------------|--------------|
|NAV App| Published Application|
|NAV App Object Metadata| Application Object Metadata|
|NAV App Resource| Application Resource|
|NAV App Dependencies| Application Dependency|
|NAV App Tenant App| Installed Application|

> [!IMPORTANT]
> The TempBLOB table is marked with `ObsoleteState:Pending`, however, we will remove the table in 2021 release wave 2. If you have code that depends on the TempBLOB table, you must rewrite it before 2021 release wave 2 becomes available. For example, consider using the BLOB Storage module in the System Application instead.

## See Also

[Deprecated Features in the Base App](deprecated-features-w1.md)  
[Deprecated Features in the Platform - Clients, Server, and Database](deprecated-features-platform.md)  
[Technical Upgrade](upgrade-technical-upgrade-v15-v16.md)  
[Best Practices for Deprecation of Code in the Base App](../developer/devenv-deprecation-guidelines.md)  
[Microsoft Timeline for Deprecating Code in Business Central](../developer/devenv-deprecation-timeline.md)  
