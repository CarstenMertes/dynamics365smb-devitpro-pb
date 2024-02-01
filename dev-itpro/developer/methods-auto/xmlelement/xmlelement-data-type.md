---
title: "XmlElement Data Type"
description: "Represents an XML element."
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
# XmlElement Data Type
> **Version**: _Available or changed with runtime version 1.0._

Represents an XML element.


## Static methods
The following methods are available on the XmlElement data type.


|Method name|Description|
|-----------|-----------|
|[Create(Text)](xmlelement-create-string-method.md)|Creates an XmlElement node.|
|[Create(Text, Text)](xmlelement-create-string-string-method.md)|Creates an XmlElement node.|
|[Create(Text, Text, Any,...)](xmlelement-create-string-string-joker-method.md)|Creates an XmlElement node.|
|[Create(Text, Any,...)](xmlelement-create-string-joker-method.md)|Creates an XmlElement node.|

## Instance methods
The following methods are available on instances of the XmlElement data type.

|Method name|Description|
|-----------|-----------|
|[Add(Any,...)](xmlelement-add-method.md)|Adds the specified content as a child of this element.|
|[AddAfterSelf(Any,...)](xmlelement-addafterself-method.md)|Adds the specified content immediately after this node.|
|[AddBeforeSelf(Any,...)](xmlelement-addbeforeself-method.md)|Adds the specified content immediately before this node.|
|[AddFirst(Any,...)](xmlelement-addfirst-method.md)|Adds the specified content at the start of the child list of this element.|
|[AsXmlNode()](xmlelement-asxmlnode-method.md)|Converts the node to an XmlNode.|
|[Attributes()](xmlelement-attributes-method.md)|Gets a collection of the attributes of this element.|
|[GetChildElements()](xmlelement-getchildelements--method.md)|Gets a list containing the child elements for this element, in document order.|
|[GetChildElements(Text)](xmlelement-getchildelements-string-method.md)|Gets a list containing the child elements for this element, in document order.|
|[GetChildElements(Text, Text)](xmlelement-getchildelements-string-string-method.md)|Gets a list containing the child elements for this element, in document order.|
|[GetChildNodes()](xmlelement-getchildnodes-method.md)|Gets a list containing the child elements for this element, in document order.|
|[GetDescendantElements()](xmlelement-getdescendantelements--method.md)|Gets a list containing the descendant elements for this element, in document order.|
|[GetDescendantElements(Text)](xmlelement-getdescendantelements-string-method.md)|Gets a list containing the descendant elements for this element, in document order.|
|[GetDescendantElements(Text, Text)](xmlelement-getdescendantelements-string-string-method.md)|Gets a list containing the descendant elements for this element, in document order.|
|[GetDescendantNodes()](xmlelement-getdescendantnodes-method.md)|Gets a list containing the descendant nodes for this element, in document order.|
|[GetDocument(var XmlDocument)](xmlelement-getdocument-method.md)|Gets the XmlDocument for this node.|
|[GetNamespaceOfPrefix(Text, var Text)](xmlelement-getnamespaceofprefix-method.md)|Gets the namespace associated with a particular prefix for this element.|
|[GetParent(var XmlElement)](xmlelement-getparent-method.md)|Gets the parent XmlElement of this node.|
|[GetPrefixOfNamespace(Text, var Text)](xmlelement-getprefixofnamespace-method.md)|Gets the prefix associated with a namespace URI for this element.|
|[HasAttributes()](xmlelement-hasattributes-method.md)|Gets a boolean value indicating whether this element has at least one attribute.|
|[HasElements()](xmlelement-haselements-method.md)|Gets a value indicating whether this element has at least one child element.|
|[InnerText()](xmlelement-innertext-method.md)|Gets the concatenated values of the node and all its child nodes.|
|[InnerXml()](xmlelement-innerxml-method.md)|Gets the markup representing only the child nodes of this node.|
|[IsEmpty()](xmlelement-isempty-method.md)|Gets a value indicating whether this element contains no content.|
|[LocalName()](xmlelement-localname-method.md)|Gets the local name of this element.|
|[Name()](xmlelement-name-method.md)|Gets the fully qualified name of this element.|
|[NamespaceUri()](xmlelement-namespaceuri-method.md)|Gets the namespace URI of this element.|
|[Remove()](xmlelement-remove-method.md)|Removes this node from its parent element.|
|[RemoveAllAttributes()](xmlelement-removeallattributes-method.md)|Removes the attributes of this element.|
|[RemoveAttribute(Text)](xmlelement-removeattribute-string-method.md)|Removes the specified attribute from this element.|
|[RemoveAttribute(Text, Text)](xmlelement-removeattribute-string-string-method.md)|Removes the specified attribute from this element.|
|[RemoveAttribute(XmlAttribute)](xmlelement-removeattribute-xmlattribute-method.md)|Removes the specified attribute from this element.|
|[RemoveNodes()](xmlelement-removenodes-method.md)|Removes the child nodes from this element.|
|[ReplaceNodes(Any,...)](xmlelement-replacenodes-method.md)|Replaces the children nodes of this element with the specified content.|
|[ReplaceWith(Any,...)](xmlelement-replacewith-method.md)|Replaces this node with the specified content.|
|[SelectNodes(Text, var XmlNodeList)](xmlelement-selectnodes-string-xmlnodelist-method.md)|Selects a list of nodes matching the XPath expression.|
|[SelectNodes(Text, XmlNamespaceManager, var XmlNodeList)](xmlelement-selectnodes-string-xmlnamespacemanager-xmlnodelist-method.md)|Selects a list of nodes matching the XPath expression.|
|[SelectSingleNode(Text, var XmlNode)](xmlelement-selectsinglenode-string-xmlnode-method.md)|Selects the first XmlNode that matches the XPath expression.|
|[SelectSingleNode(Text, XmlNamespaceManager, var XmlNode)](xmlelement-selectsinglenode-string-xmlnamespacemanager-xmlnode-method.md)|Selects the first XmlNode that matches the XPath expression.|
|[SetAttribute(Text, Text)](xmlelement-setattribute-string-string-method.md)|Sets the value of the specified attribute or create it if is not part of the element's attribute collection.|
|[SetAttribute(Text, Text, Text)](xmlelement-setattribute-string-string-string-method.md)|Sets the value of the specified attribute or create it if is not part of the element's attribute collection.|
|[WriteTo(OutStream)](xmlelement-writeto-outstream-method.md)|Serializes and saves the current node to the given variable.|
|[WriteTo(XmlWriteOptions, OutStream)](xmlelement-writeto-xmlwriteoptions-outstream-method.md)|Serializes and saves the current node to the given variable.|
|[WriteTo(var Text)](xmlelement-writeto-text-method.md)|Serializes and saves the current node to the given variable.|
|[WriteTo(XmlWriteOptions, var Text)](xmlelement-writeto-xmlwriteoptions-text-method.md)|Serializes and saves the current node to the given variable.|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  