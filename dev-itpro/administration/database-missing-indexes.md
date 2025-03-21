---
title: Missing Indexes in Business Central databases
description: Description about missing indexes and database missing indexes page
author: jswymer
ms.date: 03/21/2025
ms.topic: conceptual
ms.author: jswymer
ms.reviewer: jswymer
---

# Missing indexes in Business Central databases

This article gives an insight about missing indexes for administrators and developers. **Database Missing Indexes** help administrators and developers to enhance the performance of their applications.

## Indexes overview

[!INCLUDE[indexes_overview_md](../includes/indexes_overview.md)]

Learn more about indexes and their types in [Clustered and nonclustered indexes described](/sql/relational-databases/indexes/clustered-and-nonclustered-indexes-described).

## Missing indexes

When you run a database query, the query optimizer, which is an important database component, analyzes and chooses the best possible plan to complete the instruction. In doing so, it provides additional information about the ongoing operation that the operation might perform well if the particular column (or columns) is indexed. The SQL server's Query optimizer gets this information from Dynamic Management Views (DMV), in our case, [sys.dm_db_missing_index_details](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-details-transact-sql). *sys.dm_db_missing_index_details* returns details about missing indexes, which help you in creating right indexes.

Learn how to use missing index suggestions to tune indexes and improve query performance in [Tune nonclustered indexes with missing index suggestions](/sql/relational-databases/indexes/tune-nonclustered-missing-index-suggestions)

Learn about Dynamic Management Views (DMV) in [System Dynamic Management Views (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/system-dynamic-management-views).

Learn how AL plays a part in efficient data access with SQL components in [Efficient data access](../performance/performance-developer.md#efficient-data-access).

## Database missing indexes in [!INCLUDE[prod_short](../developer/includes/prod_short.md)]

To get information on missing indexes, go to the **Database Missing Indexes** page in Business Central, and you view the data in the following columns:

|Column|Description|
|------|-----------|
| **Table Name**|The name of the table on which the suggested columns are based.|
| **Extension Id**|The ID of your application to which this data is related.|
|**Index Equality Columns**|The data in these columns is based on equality queries. For example, “Select * from customer where id = 021”|
| **Index Inequality Columns**|The data in these columns comes from queries, which aren't based on equality operations. For example, `Select * from customer where id < 200`|
| **Index Include Columns**|These columns have a copy of associated data for fast retrieval of information, which is based on the columns suggested in `Index Equality Columns` and `Index Inequality Columns`. Include columns aren't indexed columns themselves but point to the additional information linked to the indexed columns. For example, they include the fields in the `Select` part.|
| **Seeks**`\*|Number of seeks caused by queries that could have used the suggested index.|
| **Scans**\*|Number of scans caused by queries that could have used the suggested index.|
|**Average Total Costs**\*|Average cost of the queries that would be reduced if the suggested index was added.|
| **Average Impact**\*|Average percentage benefit for queries if the suggested index was added. The value means that the cost would drop on average by this percentage if the suggested index was added.|
| **Estimated Benefit**\*|The estimated benefit of adding the suggested index, which calculated as: (seeks + scans) x (average total costs) x (average impact). For example, currently the query seeks 5 times and scans 10 times and the cost is now 10 but would drop 50% if the index is added, then benefit is (5 + 10) x 10 x 50. |

\*Applies to 2025 release wave 1 (version 26.0) and later

> [!IMPORTANT]
> The information provided on the **Database Missing Indexes** page is a suggestion and isn't mandatory. Analyze where and how many indexes are best suited for optimal performance of your application. Indexes take storage space, can affect updates for tables with frequent insertions and deletions, and can be an expensive operation if overused.

## Related information

[Performance Article For Developers](../performance/performance-developer.md)  
[Optimizing SQL Server Performance with Business Central](optimize-sql-server-performance.md)  
[How to tune indexes with missing index suggestions](/sql/relational-databases/indexes/tune-nonclustered-missing-index-suggestions)
