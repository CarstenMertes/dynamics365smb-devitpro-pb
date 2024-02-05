---
title: "Record.Next([Integer]) Method"
description: "Steps through a specified number of records and retrieves a record."
ms.author: solsen
ms.custom: na
ms.date: 03/02/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Record.Next([Integer]) Method
> **Version**: _Available or changed with runtime version 1.0._

Steps through a specified number of records and retrieves a record.


## Syntax
```AL
[Steps := ]  Record.Next([Steps: Integer])
```
## Parameters
*Record*  
&emsp;Type: [Record](record-data-type.md)  
An instance of the [Record](record-data-type.md) data type.  

*[Optional] Steps*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
Specifies the direction of the search and how many records to step over. This parameter follows the following rules:
-   \> 0  Search Steps records forward in the table.
-   \< 0  Search Steps records backward in the table.
-   = 0  Stay on the same record in the table.
If you do not specify this parameter, then the next record is found.  


## Return Value
*[Optional] Steps*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[Record Data Type](record-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  
[AL Database Methods and Performance on SQL Server](../../../administration/optimize-sql-al-Database-methods-and-performance-on-server.md)  