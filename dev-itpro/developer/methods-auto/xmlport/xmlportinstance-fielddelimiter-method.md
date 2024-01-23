---
title: "Xmlport.FieldDelimiter([Text]) Method"
description: "Gets and sets the FiledDelimiter used when running, importing or exporting the XmlPort."
ms.author: solsen
ms.custom: na
ms.date: 03/24/2022
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Xmlport.FieldDelimiter([Text]) Method
> **Version**: _Available or changed with runtime version 1.0._

Gets and sets the FiledDelimiter used when running, importing or exporting the XmlPort.


## Syntax
```AL
[Delimiter := ]  Xmlport.FieldDelimiter([Delimiter: Text])
```
> [!NOTE]
> This method can be invoked using property access syntax.
## Parameters
*Xmlport*  
&emsp;Type: [Xmlport](xmlport-data-type.md)  
An instance of the [Xmlport](xmlport-data-type.md) data type.  

*[Optional] Delimiter*  
&emsp;Type: [Text](../text/text-data-type.md)  
The new value of the FieldDelimiter.  


## Return Value
*[Optional] Delimiter*  
&emsp;Type: [Text](../text/text-data-type.md)  
The FieldDelimiter used when running, importing or exporting the XmlPort.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[Xmlport Data Type](xmlport-data-type.md)  
[FieldDelimiter Property](../../properties/devenv-fielddelimiter-property.md)   
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)