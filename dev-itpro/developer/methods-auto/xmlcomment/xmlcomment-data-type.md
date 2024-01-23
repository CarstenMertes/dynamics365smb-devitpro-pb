---
title: "XmlComment Data Type"
description: "Represents an XML comment."
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
# XmlComment Data Type
> **Version**: _Available or changed with runtime version 1.0._

Represents an XML comment.


## Static methods
The following methods are available on the XmlComment data type.


|Method name|Description|
|-----------|-----------|
|[Create(Text)](xmlcomment-create-method.md)|Creates an XmlComment node.|

## Instance methods
The following methods are available on instances of the XmlComment data type.

|Method name|Description|
|-----------|-----------|
|[AddAfterSelf(Any,...)](xmlcomment-addafterself-method.md)|Adds the specified content immediately after this node.|
|[AddBeforeSelf(Any,...)](xmlcomment-addbeforeself-method.md)|Adds the specified content immediately before this node.|
|[AsXmlNode()](xmlcomment-asxmlnode-method.md)|Converts the node to an XmlNode.|
|[GetDocument(var XmlDocument)](xmlcomment-getdocument-method.md)|Gets the XmlDocument for this node.|
|[GetParent(var XmlElement)](xmlcomment-getparent-method.md)|Gets the parent XmlElement of this node.|
|[Remove()](xmlcomment-remove-method.md)|Removes this node from its parent element.|
|[ReplaceWith(Any,...)](xmlcomment-replacewith-method.md)|Replaces this node with the specified content.|
|[SelectNodes(Text, var XmlNodeList)](xmlcomment-selectnodes-string-xmlnodelist-method.md)|Selects a list of nodes matching the XPath expression.|
|[SelectNodes(Text, XmlNamespaceManager, var XmlNodeList)](xmlcomment-selectnodes-string-xmlnamespacemanager-xmlnodelist-method.md)|Selects a list of nodes matching the XPath expression.|
|[SelectSingleNode(Text, var XmlNode)](xmlcomment-selectsinglenode-string-xmlnode-method.md)|Selects the first XmlNode that matches the XPath expression.|
|[SelectSingleNode(Text, XmlNamespaceManager, var XmlNode)](xmlcomment-selectsinglenode-string-xmlnamespacemanager-xmlnode-method.md)|Selects the first XmlNode that matches the XPath expression.|
|[Value([Text])](xmlcomment-value-method.md)|Gets or sets the string value of this comment.|
|[WriteTo(OutStream)](xmlcomment-writeto-outstream-method.md)|Serializes and saves the current node to the given variable.|
|[WriteTo(XmlWriteOptions, OutStream)](xmlcomment-writeto-xmlwriteoptions-outstream-method.md)|Serializes and saves the current node to the given variable.|
|[WriteTo(var Text)](xmlcomment-writeto-text-method.md)|Serializes and saves the current node to the given variable.|
|[WriteTo(XmlWriteOptions, var Text)](xmlcomment-writeto-xmlwriteoptions-text-method.md)|Serializes and saves the current node to the given variable.|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  