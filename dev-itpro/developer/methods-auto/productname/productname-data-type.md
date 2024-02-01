---
title: "ProductName Data Type"
description: "An application can have a full name, marketing name, and short name."
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
# ProductName Data Type
> **Version**: _Available or changed with runtime version 1.0._

An application can have a full name, marketing name, and short name. The PRODUCTNAME functions enable you to retrieve these name variations.


## Static methods
The following methods are available on the ProductName data type.


|Method name|Description|
|-----------|-----------|
|[Full()](productname-full-method.md)|FULL returns a text string that contains the application's full name.|
|[Marketing()](productname-marketing-method.md)|MARKETING returns a text string that contains the application's marketing name.|
|[Short()](productname-short-method.md)|SHORT returns a text string that contains the application's short name.|


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks
You define the different name variations for an application in the `navsettings.json` configuration file. For more information, see [Configuring Business Central Web Server Instances](../../../administration/configure-web-server.md).

## See Also
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  
