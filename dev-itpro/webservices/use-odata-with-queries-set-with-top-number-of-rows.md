---
title: "Using OData with Queries That are Set with a Top Number of Rows"
description: Learn about using queries that are set with a top number of rows.
ms.custom: na
ms.date: 05/26/2021
ms.reviewer: na
ms.topic: conceptual
---
# Using OData with Queries That are Set with a Top Number of Rows

[!INCLUDE[prod_short](../developer/includes/prod_short.md)] queries include the [TopNumberOfRows Property](../developer/properties/devenv-TopNumberOfRows-Property.md) and [TopNumberOfRows Method](../developer/methods-auto/query/queryinstance-topnumberofrows-method.md) that can be used to specify the maximum number of rows to include in the resulting dataset. The [!INCLUDE[server](../developer/includes/server.md)] includes the **Max Page Size** setting for OData that specifies the maximum number of entities returned per page of OData results. The default value is 20,000.  
  
To ensure that the OData results include the correct number of entities when you are using a query that is set with a top number of rows, you should set the **Max Page Size** value greater than the value that is set by the **TopNumberOfRows**  property and **TopNumberOfRows**  method. Otherwise, the **TopNumberOfRows** property and **TopNumberOfRows** method are ignored and the query dataset will be returned in the OData results.  
  
Typically, the **TopNumberOfRows** property or **TopNumberOfRows** method are used to return a relatively small number of entities, such as the top five, ten, or 100 entities. Therefore, in most cases, the value of the **TopNumberOfRows** property and **TopNumberOfRows** method will be less than the **Max Page Size**, so that you will not have to change the **Max Page Size** setting. 

> [!TIP]
> In HTTP requests, it can be beneficial to use `odata.maxpagesize` instead of the system query options `$top` and `$skip`. For instance, `odata.maxpagesize` automatically includes `nextlink` in the response, which lets you continuously retrieve a large dataset in limited chunks. 

For information about how to change the **Max Page Size** setting, see [Configuring Business Central Server](../administration/configure-server-instance.md) and [Server-Driven Paging in OData Web Services](Server-Driven-Paging-in-OData-Web-Services.md).

## See Also

[Basic Page Operations](Basic-Page-Operations.md)
