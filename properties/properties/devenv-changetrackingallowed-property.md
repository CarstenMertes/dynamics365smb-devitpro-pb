---
title: "ChangeTrackingAllowed Property"
ms.date: 10/01/2020
ms.suite: na
ms.topic: article
ms.assetid: 3e156138-d9c7-486e-b697-43da477d505a
caps.latest.revision: 8
author: SusanneWindfeldPedersen
---

# ChangeTrackingAllowed Property
Indicates whether change tracking is enabled for the entity exposed through the page. When the value of the property is set to **true**, an annotation is written in the OData metadata document which indicates that the exposed entity supports change tracking. The default is **false**.
 
## Applies to  
 - Pages
  
## Property value
**True** if the page is exposed as a service, otherwise **false**. The default is **false**.

## Syntax

```AL
ChangeTrackingAllowed = true;
```

> [!NOTE]
> The property **ChangeTrackingAllowed** can only be set if the [PageType Property](devenv-pagetype-property.md) is set to **API**.

 
## See Also  
[Properties](devenv-properties.md)  

