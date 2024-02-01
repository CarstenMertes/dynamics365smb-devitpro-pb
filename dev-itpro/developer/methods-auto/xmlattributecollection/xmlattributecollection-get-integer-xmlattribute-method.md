---
title: "XmlAttributeCollection.Get(Integer, var XmlAttribute) Method"
description: "Gets the specified attribute."
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
# XmlAttributeCollection.Get(Integer, var XmlAttribute) Method
> **Version**: _Available or changed with runtime version 1.0._

Gets the specified attribute.


## Syntax
```AL
[Ok := ]  XmlAttributeCollection.Get(Index: Integer, var Result: XmlAttribute)
```
## Parameters
*XmlAttributeCollection*  
&emsp;Type: [XmlAttributeCollection](xmlattributecollection-data-type.md)  
An instance of the [XmlAttributeCollection](xmlattributecollection-data-type.md) data type.  

*Index*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The index of the attribute to retrieve.  

*Result*  
&emsp;Type: [XmlAttribute](../xmlattribute/xmlattribute-data-type.md)  
Variable containing the requested XmlAttribute if the operation is successful.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the operation was successful; otherwise **false**.   If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[XmlAttributeCollection Data Type](xmlattributecollection-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)