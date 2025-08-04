---
title: Resolving Page 2500 Compilation Error
description: Explains how to resolve the compilation errors that you get for Page 2500 when converting a database from Dynamics NAV to Business Central.
ms.custom: evergreen
ms.date: 04/18/2024
ms.update-cycle: 1095-days
ms.reviewer: jswymer
ms.topic: concept-article
author: jswymer
---
# Resolving Page 2500 Compilation Error

This article explains how to resolve the compilation error that you get for page **2500 Page Management** when converting a [!INCLUDE[nav2018_md](../developer/includes/nav2018_md.md)] database to  [!INCLUDE[prodhort](../developer/includes/prod_short.md)].

## Resolution

In the `Download Source -OnAction` trigger, replace the following code:

```
Designer.GenerateDesignerPackageZipStream(NvOutStream,ID);
```

With:

```
Designer.GenerateDesignerPackageZipStreamByVersion(NvOutStream,ID,VersionString);
```
## Related information  
 [Converting a Database](Converting-a-Database.md)  
 [Resolving Compilation Errors When Converting a Dynamics NAV 2018 Database](Resolve-Compile-Errors-When-Converting-Dynamics-NAV-2018-Database.md)  
