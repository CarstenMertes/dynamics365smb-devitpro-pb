---
title: "MinimumHeight Property"
ms.date: 10/01/2020
ms.suite: na
ms.topic: article
ms.assetid: dd671414-a7c3-44bd-a860-a8bda61c7913
caps.latest.revision: 15
author: SusanneWindfeldPedersen
---

# MinimumHeight Property

Specifies the minimum size in pixels to which the control add-in can dynamically decrease its height.

## Applies to 

- Control add-in objects
  
## Value Type 
  
- Integer 

## Property Values 

The default is 0. If [VerticalShrink](devenv-verticalshrink-property.md) is **true** but MinimumHeight is 0, the control add-in can shrink to nothing.

## Dependent Property

This setting only applies if [VerticalShrink](devenv-verticalshrink-property.md) is set to **true**.

## Example 

```AL
RequestedHeight = 300;
VerticalShrink = true;
MinimumHeight = 150;
```

## See Also  

[Control Add-In Object](../devenv-control-addin-object.md)   
 