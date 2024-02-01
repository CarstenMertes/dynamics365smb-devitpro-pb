---
title: "Promoted (Profile) Property"
ms.custom: na
ms.date: 04/01/2021
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---

# Promoted (Profile) Property
> **Version**: _Available from runtime version 1.0._

<!-- this topic is manually created, parent node is devenv-promoted-property.md -->

For profiles the **Promoted** property specifies whether or not the profile is available in the **Role Explorer** to the user. **Promoted** can also be set on Page Actions, see [Promoted (Actions) Property](devenv-promoted-action-property.md).
  
## Applies to  
  
- Profiles
  
## Property Value  

**True** if the profile is available from the **Role Explorer** in the UI; otherwise, **false**. The default is **false**.  

## Example

The following code illustrates how to set the **Promoted** property.
 
```AL
profile MyProfile
{ 
    Description = 'Some internal comment that only the Dev can see'; 
    Caption = 'My User-friendly Name'; 
    ProfileDescription = 'A detailed description of who is this profile for, why/how to use it (etc)' 
    RoleCenter = MyRoleCenter; 
    Enabled = true; 
    Promoted = true; 
    Customizations = MyCustomization;
} 
```

## See Also  

[Properties](devenv-properties.md)  
[Promoted (Actions) Property](devenv-promoted-action-property.md) 