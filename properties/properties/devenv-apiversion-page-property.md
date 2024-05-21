---
title: "APIVersion Property - Page"
ms.author: solsen
ms.date: 10/01/2020
ms.suite: na
ms.topic: article
author: SusanneWindfeldPedersen
---
 
# APIVersion Property (Page)
Sets the version(s) of the API endpoint the page is exposed in. The syntax for providing versions is illustrated in the example below:

## Applies to  

- Page object 

## Syntax
```AL
APIVersion = 'beta', 'v1.0';
```

>[!NOTE]
> The property **APIVersion** can only be set if the [PageType Property](devenv-pagetype-property.md) is set to **API**. For more information, see [API Page Type](../devenv-api-pagetype.md).


## See Also  
[Properties](devenv-properties.md)   
[Page Object](../devenv-page-object.md)  
[APIVersion Property (Query)](devenv-apiversion-query-property.md) 
