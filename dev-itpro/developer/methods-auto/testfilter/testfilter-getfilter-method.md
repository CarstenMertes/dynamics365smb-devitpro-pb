---
title: "TestFilter.GetFilter(TestFilterField) Method"
description: "Gets the filter that is applied to the specified field in a data set that is displayed on a test page."
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
# TestFilter.GetFilter(TestFilterField) Method
> **Version**: _Available or changed with runtime version 1.0._

Gets the filter that is applied to the specified field in a data set that is displayed on a test page.


## Syntax
```AL
String :=   TestFilter.GetFilter(Field: TestFilterField)
```
## Parameters
*TestFilter*  
&emsp;Type: [TestFilter](testfilter-data-type.md)  
An instance of the [TestFilter](testfilter-data-type.md) data type.  

*Field*  
&emsp;Type: [TestFilterField](../testfilterfield/testfilterfield-data-type.md)  
The field that you want to get the filter from.  


## Return Value
*String*  
&emsp;Type: [Text](../text/text-data-type.md)  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[TestFilter Data Type](testfilter-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)