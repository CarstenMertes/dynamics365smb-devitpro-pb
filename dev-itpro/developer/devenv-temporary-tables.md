---
title: "Temporary tables"
description: Learn about temporary tables in Business Central 
ms.custom: bap-template
ms.date: 02/24/2023
ms.reviewer: solsen

ms.topic: conceptual
author: SusanneWindfeldPedersen
ms.author: solsen
---

# Temporary tables

A temporary table is a temporary variable that holds a table. A temporary table is used as a buffer or intermediate storage for table data.

You can use a temporary table just like you use a database table. The differences between a temporary table and a database table are as follows:  

- A temporary table data isn't stored in the database. It's only held in memory until the table is closed.  

- The write transaction principle that applies to a database table doesn't apply to a temporary table.  

> [!TIP]  
> With [!INCLUDE [prod_short](includes/prod_short.md)] 2023 release wave 1 IntelliSense, tooltips, and CodeLens displays a suffix after the table name to indicate when a table is a temporary table.

## Advantage of using a temporary table  

The advantage of using a temporary table is that all the interaction with a temporary table occurs on [!INCLUDE[prod_long](includes/prod_long.md)]. A temporary table reduces the load on both the network and the SQL database server.  

When you want to do many operations on the data in a specific database table, you can load the data into a temporary table when you modify it. Loading the data into a temporary table speeds up the process because all the operations are done in memory on the [!INCLUDE[server](includes/server.md)].

For endpoint performance and temporary tables, see [Anti-patterns (don't do this)](../performance/performance-developer.md#general-anti-patterns-dont-do-this).

## Creating and using a temporary table

There are three ways to implement a temporary table:

- Setting the [TableType property](properties/devenv-tabletype-property.md) on the table object to **Temporary**.
- Using a temporary record variable.
- Setting the [SourceTableTemporary property](properties/devenv-sourcetabletemporary-property.md) on a page.

Whichever way you choose, you must create the [table object](devenv-table-object.md) that defines the fields, like any other table object. The differences are explained in the following sections.

> [!TIP]
> Temporary tables retain system fields, like SystemID and data audit fields. For more information, see [System Fields](devenv-table-system-fields.md).

## Setting the TableType to Temporary

[!INCLUDE[2020_releasewave2.md](../includes/2020_releasewave2.md)]

With this implementation, a physical table isn't created in the database. In the table object, set the `TableType` property to `Temporary`:

```AL
table 50100 MyTable
{
    DataClassification = ToBeClassified;
    TableType = Temporary;

    fields
    
    ...
}
```

This implementation has the same effect as using a temporary record variable or setting the SourceTableTemporary property on a page. But the advantage is that the table schema isn't synchronized with the database. So it doesn't have restrictions on breaking schema changes, like removing a field, changing its data type or length.

It will also improve the performance of BACPAC generation using the sqlpackage command-line tool, compared to temporary tables based on temporary record variables and pages. For more information, see [Performance of BACPAC generation](../performance/performance-onprem.md#performance-of-bacpac-generation).

#### Changing the table type

You can change from **Normal** to **Temporary**, and the other way around. When changing **Normal** to **Temporary** the table, you'll have to synchronize the extension with the database. This step will remove the table from the database. So if the table contains data, you'll have to synchronize the schema using the ForceSync mode.

> [!NOTE]  
> Changing the table type is considered a destructive change. So this change can only be done with [!INCLUDE[prod_short](includes/prod_short.md)] on-premises.  

## Using a temporary record variable

With this implementation, a physical table isn't created in the database. You create a global or local variable of the type record and set the [Temporary Property](./properties/devenv-properties.md) next to it. The variable that holds a temporary table is defined just like any other global or local variable. The syntax is shown in the following example:

```AL
var
    TempInvoicePostBuffer: Record "Invoice Post. Buffer" temporary;
```

You manipulate the temporary table variable as you would with any other database table. For example, you can apply filters and do searches. For more information about the operations you can do, see [Record Data Type](methods-auto/record/record-data-type.md).

## Using a SourceTableTemporary property on page objects

Another option for temporary tables is to set the [SourceTableTemporary](properties/devenv-sourcetabletemporary-property.md) on all pages that use the table. This implementation will also use a physical table in the database.

```AL
page 50100 MyPage
{
    PageType = Card;
    ApplicationArea = All;
    UsageCategory = Administration;
    SourceTable = TableName;
    SourceTableTemporary = true;
    
    layout

    ...
}
```

## Temporary tables on reports and XMLPorts

You can also use temporary tables for storing the data set that's returned by a report object or imported by an XMLPort. To do so, set the **UseTemporary property** to **true** on the relevant report data item or XMLPort table element. For more information, see [UseTemporary Property \(XMLports\)](properties/devenv-usetemporary-xmlport-property.md) and [UseTemporary Property \(Reports\)](properties/devenv-usetemporary-report-property.md).  

Temporary tables are useful on reports when the column data isn't mapped directly to a field in the database. But instead, the data is a result of a process or operation. For example, suppose the column was an aggregation of data from several columns. If a temporary table isn't used, the data must be handled by AL code.

For XMLPorts, if the data that you're importing has a different structure than the table in [!INCLUDE[d365fin_long_md](includes/d365fin_long_md.md)] that you want to insert it into, you can import the data into a temporary table. You can then modify the data before inserting it into the database.

## See Also

[Get Started with AL](devenv-get-started.md)  
[Table Object](devenv-table-object.md)  
[Temporary Property](./properties/devenv-properties.md)  
[UseTemporary Property (Report)](properties/devenv-usetemporary-report-property.md)  
[UseTemporary Property (XMLPort)](properties/devenv-usetemporary-xmlport-property.md)