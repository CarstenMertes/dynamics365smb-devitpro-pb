---
title: "XmlNamespaceManager Data Type"
description: "Represents a namespace manager that can be used to resolve, add and remove namespaces to a collection."
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
# XmlNamespaceManager Data Type
> **Version**: _Available or changed with runtime version 1.0._

Represents a namespace manager that can be used to resolve, add and remove namespaces to a collection. It also provides scope management for these namespaces.



## Instance methods
The following methods are available on instances of the XmlNamespaceManager data type.

|Method name|Description|
|-----------|-----------|
|[AddNamespace(Text, Text)](xmlnamespacemanager-addnamespace-method.md)|Adds the given namespace to the collection.|
|[HasNamespace(Text)](xmlnamespacemanager-hasnamespace-method.md)|Gets a value indicating whether the supplied prefix has a namespace defined for the current scope.|
|[LookupNamespace(Text, var Text)](xmlnamespacemanager-lookupnamespace-method.md)|Gets the namespace URI for the specified prefix.|
|[LookupPrefix(Text, var Text)](xmlnamespacemanager-lookupprefix-method.md)|Finds the prefix declared for the given namespace URI.|
|[NameTable([XmlNameTable])](xmlnamespacemanager-nametable-method.md)|Gets or sets the XmlNameTable associated with this object.|
|[PopScope()](xmlnamespacemanager-popscope-method.md)|Pops a namespace scope off the stack.|
|[PushScope()](xmlnamespacemanager-pushscope-method.md)|Pushes a namespace scope onto the stack.|
|[RemoveNamespace(Text, Text)](xmlnamespacemanager-removenamespace-method.md)|Removes the given namespace for the given prefix.|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  