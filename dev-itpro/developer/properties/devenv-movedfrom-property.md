---
title: "MovedFrom property"
description: "Specifies the origin extension ID when a table is moved to a new extension."
ms.author: solsen
ms.date: 08/26/2024
ms.topic: reference
author: SusanneWindfeldPedersen
ms.reviewer: solsen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# MovedFrom Property
> **Version**: _Available or changed with runtime version 12.0._

Specifies the origin extension ID when a table is moved to a new extension. If the source table exists in the database during the sync operation, the table will be moved to this extension along with all its data. Otherwise, a new table will be created in the database.

## Applies to
-   Table
-   Table field

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

Tables and fields can be moved between extensions by using the `MovedFrom` and `MovedTo` properties. This is useful when you want to reorganize your extensions or when you need to move a table from one extension to another without losing the data.

Learn more in [Moving tables and fields between extensions](../devenv-move-table-fields-between-extensions.md).

## Related information  
[Getting Started with AL](../devenv-get-started.md)  
[Developing Extensions](../devenv-dev-overview.md)  