---
title: "Record.CalcSums(Any [, Any,...]) Method"
description: "Calculates the total of a column in a table."
ms.author: solsen
ms.custom: na
ms.date: 06/15/2021
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Record.CalcSums(Any [, Any,...]) Method
> **Version**: _Available or changed with runtime version 1.0._

Calculates the total of a column in a table. You specify which fields to calculate by using parameters.


## Syntax
```AL
[Ok := ]  Record.CalcSums(Field1: Any [, Field2: Any,...])
```
## Parameters
*Record*  
&emsp;Type: [Record](record-data-type.md)  
An instance of the [Record](record-data-type.md) data type.  

*Field1*  
&emsp;Type: [Any](../any/any-data-type.md)  
  
*[Optional] Field2*  
&emsp;Type: [Any](../any/any-data-type.md)  
  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the operation was successful; otherwise **false**.   If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks
If one of the fields specified is not a SumIndexField, the operation will be unsuccessful and a runtime error will occur.

## See Also
[Record Data Type](record-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  
[CALCSUM Method (FieldRef)](../fieldref/fieldref-calcsum-method.md)  
[AL Database Methods and Performance on SQL Server](../../../administration/optimize-sql-al-Database-methods-and-performance-on-server.md)