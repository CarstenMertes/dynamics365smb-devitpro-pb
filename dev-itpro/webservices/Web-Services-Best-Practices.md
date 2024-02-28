---
title: Web services best practices
description: Get the list of recommendations for how to use web services in your Business Central solution.
author: jswymer
ms.custom: bap-template
ms.date: 01/28/2024
ms.reviewer: jswymer
ms.topic: conceptual
ms.author: jswymer
---

# Web services best practices

This article provides recommendations that you can implement to make your web services applications faster and easier to understand and maintain.  
  
|Recommendation|Example|  
|--------------------|-------------|  
| Performance of web services is both the responsibility of the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] server endpoint and the consumer (the client). | Visit the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] web services performance tuning guide to learn how to make web services fast and stable. Read more at [Web Services Performance](web-service-performance.md)   |
|Use the HTTPS protocol to send data between [!INCLUDE[prod_short](../developer/includes/prod_short.md)] and the web service consumer. The examples in this section use the HTTP protocol to illustrate the setup, but we recommend that your solution uses transport-level security.|In the application that consumes the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] web service, require that URIs are accessed by using HTTPS. For example, a more secure URI for the OData web services on your local computer is `https://localhost:7048/BC230/ODataV4/`.|  
|Use singular forms of names. This provides meaningful singular entity names in the generated proxy classes.|When publishing page 21, Customer Card, use **Customer** as the service name instead of **Customers** or **CustomerCard**.|  
|Avoid using spaces and other characters because they're transformed to underscores or other characters that may not be displayed as you want and could lead to ambiguity.|When publishing page 42, Sales Order, remove the space and use **SalesOrder** as the service name.|  
|Use Pascal casing when you combine words. Pascal casing capitalizes the first character of each word, including acronyms and initialisms that are more than two letters long.|Use **SalesOrder** or **ContactPerson** as the service name.|

[!INCLUDE[gui_allowed](../developer/includes/include-gui-allowed.md)]

## See also

[Web Services Overview](web-services.md)  
[Writing fast Web Services](../performance/performance-developer.md)
