---
title: "ObjectEntitlements Property"
description: "Determines the object permissions that this entitlement object permits a user or application to use."
ms.author: solsen
ms.custom: na
ms.date: 06/15/2022
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# ObjectEntitlements Property
> **Version**: _Available or changed with runtime version 7.0._

Determines the object permissions that this entitlement object permits a user or application to use.

## Applies to
-   Entitlement

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

> [!NOTE]  
> In the current version of [!INCLUDE [prod_short](../../includes/prod_short.md)] entitlements can only be included with Microsoft apps (enforced by the AppSource cop rules and the technical validation checks that we run for the apps submitted to AppSource). These objects will become available for the ISV apps when we introduce ability to monetize AppSource apps in one of our future releases. For more information, see [Entitlement Object](../devenv-entitlement-object.md).

## Syntax

```al
entitlement MyEntitlement
{
    ...
    ObjectEntitlements = 
        ”D365 BUS PREMIUM - BaseApp”;​
}
```


## See Also

[Get Started with AL](../devenv-get-started.md)  
[Developing Extensions](../devenv-dev-overview.md)  
[Entitlement Object](../devenv-entitlement-object.md)  