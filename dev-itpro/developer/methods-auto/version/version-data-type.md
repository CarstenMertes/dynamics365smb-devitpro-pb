---
title: "Version data type"
description: "Represents a version matching the format: Major.Minor.Build.Revision ."
ms.author: solsen
ms.date: 02/18/2025
ms.topic: reference
author: SusanneWindfeldPedersen
ms.reviewer: solsen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Version Data type
> **Version**: _Available or changed with runtime version 1.0._

Represents a version matching the format: Major.Minor.Build.Revision .


## Static methods
The following methods are available on the Version data type.


|Method name|Description|
|-----------|-----------|
|[Create(Text)](version-create-string-method.md)|Creates a version object from the provided string. The string should be in the format W.X.Y.Z, where W, X, Y and Z represent positive integers and where Y and Z are optional. If the input string is not in the expected format, an exception is thrown.|
|[Create(Integer, Integer [, Integer] [, Integer])](version-create-integer-integer-integer-integer-method.md)|Creates a version object from the major, minor, build and revision numbers provided.|

## Instance methods
The following methods are available on instances of the Version data type.

|Method name|Description|
|-----------|-----------|
|[Build()](version-build-method.md)|Gets the build number of the version.|
|[Major()](version-major-method.md)|Gets the major number of the version.|
|[Minor()](version-minor-method.md)|Gets the minor number of the version.|
|[Revision()](version-revision-method.md)|Gets the revision number from the version.|
|[ToText()](version-totext-method.md)|Converts the value to a text. Equvilant to calling Format(value, 0, 0).|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## Related information  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  