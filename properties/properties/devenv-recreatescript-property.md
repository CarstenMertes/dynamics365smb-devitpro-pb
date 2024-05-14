---
title: "RecreateScript Property"
ms.date: 10/01/2020
ms.suite: na
ms.topic: article
ms.assetid: dd671414-a7c3-44bd-a860-a8bda61c7913
caps.latest.revision: 15
author: SusanneWindfeldPedersen
---

# RecreateScript Property

Specifies the script which is invoked when the control add-in is recreated.

## Applies to

- Control add-in objects.

## Property Values

A path to a single script file. The default is blank. 

## Remarks

After the hosting page has been loaded and the control add-in has been initialized, the page may need to recreate the control add-in during specific situations, such as if the user has moved the add-in during personalization.

You can use this property to optimize re-initialization of the control add-in when it has already been initialized earlier. For example, this could be used to redraw some of the visuals without the need for expensive fetching of data.

This property is optional. If left blank, the script defined by [StartupScript](devenv-startupscript-property.md) will be invoked when the control add-in is recreated. 

## Code Example

```AL
RecreateScript = 'js/chartCached.js';
```


## See Also

[Control Add-In Object](../devenv-control-addin-object.md)   
 