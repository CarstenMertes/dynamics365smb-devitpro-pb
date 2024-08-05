---
title: "DataLength Property"
ms.date: 10/01/2020
ms.suite: na
ms.topic: article
ms.assetid: 5aeb3c81-dca9-4df6-98dc-322153eca056
caps.latest.revision: 6
author: SusanneWindfeldPedersen
---

# DataLength Property

Sets the maximum length of data stored in this field.  
  
## Applies to  

- Fields  

## Syntax

```AL
field(1; City; Text[15])
```
  
## Remarks

For [Text Data Type](../datatypes/devenv-text-data-type.md) and [Code Data Type](../datatypes/devenv-code-data-type.md) fields, enter the maximum length of the field. The database only stores the actual content of the field—not the maximum length you specify.  
  
This field does not apply to the other data types because they have fixed lengths.  
  
## See Also  

[Text Data Type](../datatypes/devenv-text-data-type.md)  
[Code Data Type](../datatypes/devenv-code-data-type.md)