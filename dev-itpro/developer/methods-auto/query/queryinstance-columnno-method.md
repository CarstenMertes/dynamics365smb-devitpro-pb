---
title: "Query.ColumnNo(Any) Method"
description: "Returns the ID that is assigned to a query column in the query definition."
ms.author: solsen
ms.custom: na
ms.date: 07/07/2021
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Query.ColumnNo(Any) Method
> **Version**: _Available or changed with runtime version 1.0._

Returns the ID that is assigned to a query column in the query definition.


## Syntax
```AL
Number :=   Query.ColumnNo(Column: Any)
```
## Parameters
*Query*  
&emsp;Type: [Query](query-data-type.md)  
An instance of the [Query](query-data-type.md) data type.  

*Column*  
&emsp;Type: [Any](../any/any-data-type.md)  
Refers to the name of the query column. The name of a query column is specified by the Name Property.  


## Return Value
*Number*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The ID of the query column.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[Query Data Type](query-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)