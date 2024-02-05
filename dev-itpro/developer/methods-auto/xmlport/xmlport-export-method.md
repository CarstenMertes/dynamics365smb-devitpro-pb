---
title: "Xmlport.Export(Integer, var OutStream [, var Record]) Method"
description: "Creates an XML data stream (XML document) and sends it to a chosen destination."
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
# Xmlport.Export(Integer, var OutStream [, var Record]) Method
> **Version**: _Available or changed with runtime version 1.0._

Creates an XML data stream (XML document) and sends it to a chosen destination.


## Syntax
```AL
[Ok := ]  Xmlport.Export(Number: Integer, var OutStream: OutStream [, var Record: Record])
```
## Parameters
*Number*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The ID of the XmlPort that you want to run.  

*OutStream*  
&emsp;Type: [OutStream](../outstream/outstream-data-type.md)  
Where the XmlPort object will write the XML data stream.  

*[Optional] Record*  
&emsp;Type: [Record](../record/record-data-type.md)  
The record to use in the XmlPort. Any filters attached to the record will be used. This parameter is optional. If this parameter is omitted, all records in the table are exported.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the operation was successful; otherwise **false**.   If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[Xmlport Data Type](xmlport-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)