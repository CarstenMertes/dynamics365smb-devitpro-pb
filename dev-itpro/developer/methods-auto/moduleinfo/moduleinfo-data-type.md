---
title: "ModuleInfo Data Type"
description: "Represents information about an application consumable from AL."
ms.author: solsen
ms.custom: na
ms.date: 12/01/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# ModuleInfo Data Type
> **Version**: _Available or changed with runtime version 1.0._

Represents information about an application consumable from AL.



## Instance methods
The following methods are available on instances of the ModuleInfo data type.

|Method name|Description|
|-----------|-----------|
|[AppVersion()](moduleinfo-appversion-method.md)|Gets the version of the specified application's metadata.|
|[DataVersion()](moduleinfo-dataversion-method.md)|Gets the version of the specified application's data in the context of a given tenant. This indicates the last version that was installed or successfully upgraded to and will not match the application version if the tenant is in a data upgrade pending state.|
|[Dependencies()](moduleinfo-dependencies-method.md)|Gets the collection of application dependencies.|
|[Id()](moduleinfo-id-method.md)|Gets the ID of the specified application.|
|[Name()](moduleinfo-name-method.md)|Gets the name of the specified application.|
|[PackageId()](moduleinfo-packageid-method.md)|Gets the package ID of the specified application.|
|[Publisher()](moduleinfo-publisher-method.md)|Gets the publisher of the specified application.|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  