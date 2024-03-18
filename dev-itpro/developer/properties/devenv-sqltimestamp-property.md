---
title: "SqlTimestamp Property"
description: "Specifies a field to be a timestamp field."
ms.author: solsen
ms.custom: na
ms.date: 06/15/2022
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# SqlTimestamp Property
> **Version**: _Available or changed with runtime version 1.0._

Specifies a field to be a timestamp field.

## Applies to
-   Table Field

[//]: # (IMPORTANT: END>DO_NOT_EDIT)


## Property Value  

**True** if the field is the timestamp field; otherwise, **false**. The default value is **false**.  

## Syntax

```AL
SQLTimestamp = true;
```

## Remarks

Each table includes a hidden timestamp field. The timestamp field contains row version numbers for records as maintained in SQL Server. This property exposes the timestamp field in the table object, and enables you to write code against it. This property only applies to fields that have the data type `BigInteger`. For more information, see [Timestamp Field](../devenv-table-system-fields.md#timestamp).

## See Also  

[Properties](devenv-properties.md)   
[Table and Table Extension Properties](devenv-table-properties.md)  
