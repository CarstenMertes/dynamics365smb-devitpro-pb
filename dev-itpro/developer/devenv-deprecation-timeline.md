---
title: "Microsoft Timeline for Deprecating Code in Business Central"
description: "Description of the timeline for deprecating code in Business Central."
author: SusanneWindfeldPedersen
ms.custom: na
ms.date: 09/26/2022
ms.reviewer: solsen
ms.topic: conceptual
ms.author: solsen
---

# Microsoft Timeline for Deprecating Code in Business Central

This article provides an overview of the timeline of when to expect code to be obsoleted once you start seeing warnings when extending it. To obsolete objects, the [ObsoleteState Property](properties/devenv-obsoletestate-property.md) and [ObsoleteTag Property](properties/devenv-obsoletetag-property.md) are used to specify where and when an object is marked as obsolete, for example, branch, build, or date of obsoleting the object. For methods and variables, the [Obsolete Attribute](/dynamics365/business-central/dev-itpro/developer/attributes/devenv-obsolete-attribute) is used for the same purpose. Some of the best practices for how Microsoft deprecates code can be seen in the [Best Practices for Deprecation of Code in the Base App](devenv-deprecation-guidelines.md) article. 

When Microsoft obsoletes code, we intentionally set the obsolete tag to the version in which the element is obsoleted and not when the code will be removed. This is because our deprecation rules and timelines may change, and that releases and versioning schemes may change. Setting the version in which things are obsoleted is a statement of fact and doesn't change. 

## How long time from obsoleted to deprecated? 

When an object is marked as obsolete, another 12 months will pass before the code is removed, in some cases even longer. Microsoft doesn't set a specific date for the removal due to engineering and architectural considerations. So, once you start getting warnings the feature or code won't be deprecated for at least two versions. If the tag is set to, for example, `'18.0'`, the code will still be present in versions 19 and 20. We'll at the earliest remove the code in version 21.

## When should I start refactoring?

When a major update of [!INCLUDE[prod_short](../includes/prod_short.md)] is released, and you start seeing deprecation warnings, it's encouraged to begin removing dependencies by refactoring the code. This work is important to do because once Microsoft does remove the code, the dependent app will be broken if it hasn't been refactored.

If you want to validate that your extension doesn't reference objects that are pending obsoletion with an obsolete tag version lower than a given version, you can use the [AppSourceCop](analyzers/appsourcecop.md) by setting the `obsoleteTagMinAllowedMajorMinor` in the AppSourceCop.json. For more information, see [AS0105](analyzers/appsourcecop-as0105.md).

## See Also

[AL Development Environment](devenv-reference-overview.md)  
[Directives in AL](directives/devenv-directives-in-al.md)  
[Best Practices for Deprecation of Code in the Base App](devenv-deprecation-guidelines.md)  
[ObsoleteTag Property](properties/devenv-obsoletetag-property.md)  
[ObsoleteState Property](properties/devenv-obsoletestate-property.md)  
[ObsoleteReason Property](properties/devenv-obsoletereason-property.md)  
[Obsolete Attribute](/dynamics365/business-central/dev-itpro/developer/attributes/devenv-obsolete-attribute)
