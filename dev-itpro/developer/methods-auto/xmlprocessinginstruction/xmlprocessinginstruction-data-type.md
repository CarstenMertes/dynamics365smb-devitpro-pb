---
title: "XmlProcessingInstruction Data Type"
description: "Represents a processing instruction, which XML defines to keep processor-specific information in the text of the document."
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
# XmlProcessingInstruction Data Type
> **Version**: _Available or changed with runtime version 1.0._

Represents a processing instruction, which XML defines to keep processor-specific information in the text of the document.


## Static methods
The following methods are available on the XmlProcessingInstruction data type.


|Method name|Description|
|-----------|-----------|
|[Create(Text, Text)](xmlprocessinginstruction-create-method.md)|Creates an XmlProcessingInstruction node.|

## Instance methods
The following methods are available on instances of the XmlProcessingInstruction data type.

|Method name|Description|
|-----------|-----------|
|[AddAfterSelf(Any,...)](xmlprocessinginstruction-addafterself-method.md)|Adds the specified content immediately after this node.|
|[AddBeforeSelf(Any,...)](xmlprocessinginstruction-addbeforeself-method.md)|Adds the specified content immediately before this node.|
|[AsXmlNode()](xmlprocessinginstruction-asxmlnode-method.md)|Converts the node to an XmlNode.|
|[GetData(var Text)](xmlprocessinginstruction-getdata-method.md)|Gets the content of the processing instruction, excluding the target.|
|[GetDocument(var XmlDocument)](xmlprocessinginstruction-getdocument-method.md)|Gets the XmlDocument for this node.|
|[GetParent(var XmlElement)](xmlprocessinginstruction-getparent-method.md)|Gets the parent XmlElement of this node.|
|[GetTarget(var Text)](xmlprocessinginstruction-gettarget-method.md)|Gets the target of the processing instruction.|
|[Remove()](xmlprocessinginstruction-remove-method.md)|Removes this node from its parent element.|
|[ReplaceWith(Any,...)](xmlprocessinginstruction-replacewith-method.md)|Replaces this node with the specified content.|
|[SelectNodes(Text, var XmlNodeList)](xmlprocessinginstruction-selectnodes-string-xmlnodelist-method.md)|Selects a list of nodes matching the XPath expression.|
|[SelectNodes(Text, XmlNamespaceManager, var XmlNodeList)](xmlprocessinginstruction-selectnodes-string-xmlnamespacemanager-xmlnodelist-method.md)|Selects a list of nodes matching the XPath expression.|
|[SelectSingleNode(Text, var XmlNode)](xmlprocessinginstruction-selectsinglenode-string-xmlnode-method.md)|Selects the first XmlNode that matches the XPath expression.|
|[SelectSingleNode(Text, XmlNamespaceManager, var XmlNode)](xmlprocessinginstruction-selectsinglenode-string-xmlnamespacemanager-xmlnode-method.md)|Selects the first XmlNode that matches the XPath expression.|
|[SetData(Text)](xmlprocessinginstruction-setdata-method.md)|Sets the content of the processing instruction, excluding the target.|
|[SetTarget(Text)](xmlprocessinginstruction-settarget-method.md)|Sets the target of the processing instruction.|
|[WriteTo(OutStream)](xmlprocessinginstruction-writeto-outstream-method.md)|Serializes and saves the current node to the given variable.|
|[WriteTo(XmlWriteOptions, OutStream)](xmlprocessinginstruction-writeto-xmlwriteoptions-outstream-method.md)|Serializes and saves the current node to the given variable.|
|[WriteTo(var Text)](xmlprocessinginstruction-writeto-text-method.md)|Serializes and saves the current node to the given variable.|
|[WriteTo(XmlWriteOptions, var Text)](xmlprocessinginstruction-writeto-xmlwriteoptions-text-method.md)|Serializes and saves the current node to the given variable.|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  