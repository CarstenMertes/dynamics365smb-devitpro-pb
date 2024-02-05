---
title: "APIGroup Property (Page)"
description: "Sets the group of the API endpoint that the page is exposed in."
ms.author: solsen
ms.custom: na
ms.date: 04/01/2021
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---

# APIGroup Property (Page)

<!-- this topic is manually created, parent node is devenv-apigroup-property.md -->

> **Version**: _Available from runtime version 1.0._

Sets the group of the API endpoint the page is exposed in.  The syntax for providing versions is illustrated in the example below:

## Applies to  

- Page object 

## Syntax
```AL
APIGroup = 'app1';
```

> [!NOTE]  
> The property **APIGroup** can only be set if the [PageType Property](devenv-pagetype-property.md) is set to **API**. For more information, see [API Page Type](../devenv-api-pagetype.md).

## See Also  

[Properties](devenv-properties.md)   
[Page Object](../devenv-page-object.md)  
[APIGroup Property (Query)](devenv-apigroup-query-property.md)  