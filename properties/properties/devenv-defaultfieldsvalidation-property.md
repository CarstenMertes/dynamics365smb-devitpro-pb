---
title: "DefaultFieldsValidation Property"
ms.date: 10/01/2020
ms.suite: na
ms.topic: article
author: SusanneWindfeldPedersen
---

# DefaultFieldsValidation Property

Sets a value that indicates whether fields are validated.  
  
## Applies to  

- XMLports  
  
## Property Value  

**True** if fields are validated; otherwise, **false**. The default value is **true**.

## Syntax

```AL
DefaultFieldsValidation = false;  
```
  
## Remarks

This property sets the default value of the [FieldValidate Property](devenv-fieldvalidate-property.md). Therefore, if you change the setting of the DefaultFieldsValidation property, the change is implemented for all fields. However, for fields for which the **FieldValidate** property has been set to **true** or **false**, no change is made.  
  
If you change the value of the **FieldValidate** property, the change does not affect the value of the **DefaultFieldsValidation** property. This means that **FieldValidate** can override **DefaultFieldsValidation**, but that it can also inherit the default value of **DefaultFieldsValidation**.  
  
## See Also  

[Properties](devenv-properties.md)