---
title: "TestPage.OpenNew() Method"
description: "Opens a blank test page in edit mode."
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
# TestPage.OpenNew() Method
> **Version**: _Available or changed with runtime version 1.0._

Opens a blank test page in edit mode.


## Syntax
```AL
 TestPage.OpenNew()
```

## Parameters
*TestPage*  
&emsp;Type: [TestPage](testpage-data-type.md)  
An instance of the [TestPage](testpage-data-type.md) data type.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  
 If *TestPage* is already open, then a run-time error occurs, and the outcome of the test method is FAILURE.  
  
## Example  
 This example requires that you create a TestPage variable named CustTestPage with a Subtype of Customer List and that the codeunit in which you write the code is a test codeunit.  
  
```al
// Opens a blank Customer Card test page.   
CustTestPage.OpenNEW;  
```

## See Also
[TestPage Data Type](testpage-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)