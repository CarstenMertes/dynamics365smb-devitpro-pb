---
title: Microsoft Timeline for Deprecating Code in Business Central
description: Description of the timeline for deprecating code in Business Central.
author: SusanneWindfeldPedersen
ms.date: 05/19/2025
ms.reviewer: solsen
ms.topic: concept-article
ms.author: solsen
---

# Microsoft timeline for deprecating code in Business Central

This article provides an overview of the timeline of when to expect code to be obsoleted once you start seeing warnings when extending it. To obsolete objects, the [ObsoleteState Property](properties/devenv-obsoletestate-property.md) and [ObsoleteTag Property](properties/devenv-obsoletetag-property.md) are used to specify where and when an object is marked as obsolete, for example, branch, build, or date of obsoleting the object. For methods and variables, the [Obsolete Attribute](/dynamics365/business-central/dev-itpro/developer/attributes/devenv-obsolete-attribute) is used for the same purpose. Some of the best practices for how Microsoft deprecates code can be seen in the [Best practices for deprecation of code in the Base App](devenv-deprecation-guidelines.md) article. 

When Microsoft obsoletes code, we intentionally set the obsolete tag to the version in which the element is obsoleted and not when the code will be removed. This is because our deprecation rules and timelines might change, and that releases and versioning schemes might change. Setting the version in which things are obsoleted is a statement of fact and doesn't change. 

## How long time from obsoleted to deprecated? 

When an object is marked as obsolete, another 12 months pass before the code is removed, in some cases even longer. Microsoft doesn't set a specific date for the removal due to engineering and architectural considerations. So, once you start getting warnings the feature or code isn't deprecated for at least two versions. If the tag is set to, for example, `'18.0'`, the code is still present in versions 19 and 20. We'll at the earliest remove the code in version 21.

## When should I start refactoring?

When a major update of [!INCLUDE[prod_short](../includes/prod_short.md)] is released, and you start seeing deprecation warnings, it's encouraged to begin removing dependencies by refactoring the code. This work is important to do because once Microsoft does remove the code, the dependent app is broken if it hasn't been refactored.

If you want to validate that your extension doesn't reference objects that are pending obsoletion with an obsolete tag version lower than a given version, you can use the [AppSourceCop](analyzers/appsourcecop.md) by setting the `obsoleteTagMinAllowedMajorMinor` in the AppSourceCop.json. Learn more in [AS0105](analyzers/appsourcecop-as0105.md).

## Related information

[AL Development Environment](devenv-reference-overview.md)  
[Directives in AL](directives/devenv-directives-in-al.md)  
[Best Practices for Deprecation of Code in the Base App](devenv-deprecation-guidelines.md)  
[ObsoleteTag Property](properties/devenv-obsoletetag-property.md)  
[ObsoleteState Property](properties/devenv-obsoletestate-property.md)  
[ObsoleteReason Property](properties/devenv-obsoletereason-property.md)  
[Obsolete Attribute](/dynamics365/business-central/dev-itpro/developer/attributes/devenv-obsolete-attribute)
