---
title: "CompressionType Property"
description: "Specifies the compression type used."
ms.author: solsen
ms.custom: na
ms.date: 12/08/2022
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# CompressionType Property
> **Version**: _Available or changed with runtime version 3.0._

Specifies the compression type used.

## Applies to
-   Table

## Property Value

|Value|Available or changed with|Description|
|-----------|-----------|---------------------------------------|
|**Unspecified**|runtime version 1.0|Use the compression type that is specified externally on the table, for example, in SQL Server.|
|**None**|runtime version 1.0|Do not use compression on the table.|
|**Row**|runtime version 1.0|Compress the table on a row-level.|
|**Page**|runtime version 1.0|Compress the table on a page-level. This includes row, prefix, and dictionary compression.|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Syntax

```AL
CompressionType = None|Page|Row|Unspecified; 
```

## Remarks

> [!NOTE]
> The [TableType property](devenv-tabletype-property.md) must be `Normal`. This property cannot be used on table extension objects.

With `None`, `Page`, and `Row`, the [!INCLUDE[prod_short](../includes/prod_short.md)] table synchronization process will make changes to table in SQL Server, overwriting the current compression setting in SQL Server, if any. `Unspecified` lets you control data compression directly on SQL Server or by specifying a database default compression level using the [Set-NAVTenant cmdlet](/powershell/module/microsoft.dynamics.nav.management/set-navtenant) with the `-Compression` parameter set.

For information about compression types, see [Data Compression](../../administration/optimize-sql-data-access.md#readwrite).

## Example

The following code snippet sets page-level compression on table 50100.

```AL
table 50100 MyTable
{
    TableType = Normal;
    CompressionType = Page;

    fields
    {
       ...
```

## See Also

[Properties](devenv-properties.md)  
[Page object](../devenv-page-object.md)  
[Set-NAVTenant cmdlet](/powershell/module/microsoft.dynamics.nav.management/get-navtenant)  
[Start-NAVDataCompression cmdlet](/powershell/module/microsoft.dynamics.nav.management/start-navdatabasecompression)  
