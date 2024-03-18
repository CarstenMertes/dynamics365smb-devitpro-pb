---
title: "Query.SecurityFiltering([SecurityFilter]) Method"
description: "Gets or sets how security filters are applied to the query."
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
# Query.SecurityFiltering([SecurityFilter]) Method
> **Version**: _Available or changed with runtime version 1.0._

Gets or sets how security filters are applied to the query.


## Syntax
```AL
[SecurityFiltering := ]  Query.SecurityFiltering([NewSecurityFiltering: SecurityFilter])
```
> [!NOTE]
> This method can be invoked using property access syntax.
## Parameters
*Query*  
&emsp;Type: [Query](query-data-type.md)  
An instance of the [Query](query-data-type.md) data type.  

*[Optional] NewSecurityFiltering*  
&emsp;Type: [SecurityFilter](../securityfilter/securityfilter-option.md)  
The new security filter for the query  


## Return Value
*[Optional] SecurityFiltering*  
&emsp;Type: [SecurityFilter](../securityfilter/securityfilter-option.md)  
The security filter applied to the query.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[Query Data Type](query-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)