---
title: "Query.ColumnCaption(Any) Method"
description: "Returns the current caption of a query column as a text string."
ms.author: solsen
ms.custom: na
ms.date: 03/24/2022
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Query.ColumnCaption(Any) Method
> **Version**: _Available or changed with runtime version 1.0._

Returns the current caption of a query column as a text string.


## Syntax
```AL
Caption :=   Query.ColumnCaption(Column: Any)
```
## Parameters
*Query*  
&emsp;Type: [Query](query-data-type.md)  
An instance of the [Query](query-data-type.md) data type.  

*Column*  
&emsp;Type: [Any](../any/any-data-type.md)  
Refers to the name of the query column. The name of a query column is specified by the Name Property.  


## Return Value
*Caption*  
&emsp;Type: [Text](../text/text-data-type.md)  
The query column caption.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[Query Data Type](query-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)