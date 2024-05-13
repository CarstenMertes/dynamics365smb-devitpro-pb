---
title: Configuring a Database for Read Scale-Out
description: Get tips for how to make your on-premises database ready for read scale-out.
ms.custom: bap-template
ms.date: 04/01/2021
ms.reviewer: jswymer
ms.service: dynamics-365-op
ms.topic: conceptual
author: jswymer
---
# Configuring a [!INCLUDE[prod_short.md](../developer/includes/prod_short.md)] Database for Read Scale-Out

[!INCLUDE[2020_releasewave1.md](../includes/2020_releasewave1.md)]

In the [!INCLUDE[prod_short.md](../developer/includes/prod_short.md)] Online service, read scale-out is readily available and automatically enabled on the databases.

For [!INCLUDE[prod_short.md](../developer/includes/prod_short.md)] on-premises, you must do the following steps: 

1. Check whether your database supports read scale-out.
2. Enable read scale-out on the database.

    If the [!INCLUDE[prod_short.md](../developer/includes/prod_short.md)] database runs on Azure SQL Database, determine whether the performance tier of the database supports read scale-out. You can then enable it if it's supported. For more information, see [Use read-only replicas to load-balance read-only query workloads](/azure/sql-database/sql-database-read-scale-out) in the Azure SQL Database documentation.
    
    If the [!INCLUDE[prod_short.md](../developer/includes/prod_short.md)] database runs on SQL Server, determine whether your installation supports read scale-out and how to enable the feature. For more information, see [Configure read-only routing for an Always On availability group](/sql/database-engine/availability-groups/windows/configure-read-only-routing-for-an-availability-group-sql-server) in the SQL Server documentation.
3. Enable SQL read-only replica support on the [!INCLUDE[server.md](../developer/includes/server.md)] instance.

    [!INCLUDE[server.md](../developer/includes/server.md)] includes the **Enable SQL Read-Only Replica Support** (EnableSqlReadOnlyReplicaSupport) setting. This setting isn't enabled by default. For more information, see [Configuring Business Central Server](configure-server-instance.md#Database).

## Integrating directly on SQL Server objects
[!INCLUDE[sql_integration_warning](../includes/include-sql-integrations.md)]

## See also

[Using Read Scale-Out for Better Performance](../administration/database-read-scale-out-overview.md)  
[Optimizing SQL Server Performance](../administration/optimize-sql-server-performance.md)  
[DataAccessIntent Property](../developer/properties/devenv-dataaccessintent-property.md)  
