---
title: "XmlAttributeCollection.Set(Text, Text, Text) Method"
description: "Sets the value of the specified attribute or creates it if is not part of the collection."
ms.author: solsen
ms.custom: na
ms.date: 03/02/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# XmlAttributeCollection.Set(Text, Text, Text) Method
> **Version**: _Available or changed with runtime version 1.0._

Sets the value of the specified attribute or creates it if is not part of the collection.


## Syntax
```AL
 XmlAttributeCollection.Set(LocalName: Text, NamespaceUri: Text, Value: Text)
```
## Parameters
*XmlAttributeCollection*  
&emsp;Type: [XmlAttributeCollection](xmlattributecollection-data-type.md)  
An instance of the [XmlAttributeCollection](xmlattributecollection-data-type.md) data type.  

*LocalName*  
&emsp;Type: [Text](../text/text-data-type.md)  
The local name of the attribute to set.  

*NamespaceUri*  
&emsp;Type: [Text](../text/text-data-type.md)  
The namespace URI of the attribute to set.  

*Value*  
&emsp;Type: [Text](../text/text-data-type.md)  
The value to set for the attribute.  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[XmlAttributeCollection Data Type](xmlattributecollection-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)