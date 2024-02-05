---
title: "TestRequestPage.GoToKey([Any,...]) Method"
description: "Finds the row in a data set on the test page that is identified by the specified values."
ms.author: solsen
ms.custom: na
ms.date: 07/07/2021
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# TestRequestPage.GoToKey([Any,...]) Method
> **Version**: _Available or changed with runtime version 1.0._

Finds the row in a data set on the test page that is identified by the specified values. The key is searched from the beginning of the dataset defined by the current filter. The search is performed by iterating across the rows, comparing the primary key with the primary key fields of the record. For large dataset, use SetFilter to limit the dataset.


## Syntax
```AL
[Ok := ]  TestRequestPage.GoToKey([Value: Any,...])
```
## Parameters
*TestRequestPage*  
&emsp;Type: [TestRequestPage](testrequestpage-data-type.md)  
An instance of the [TestRequestPage](testrequestpage-data-type.md) data type.  

*[Optional] Value*  
&emsp;Type: [Any](../any/any-data-type.md)  
The value or list of values to use to find the row. If this parameter is omitted, the value of the primary key that is defined for the underlying table is used.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the key is found, otherwise **false**. If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[TestRequestPage Data Type](testrequestpage-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)