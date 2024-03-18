---
title: "FileName Property"
description: "Sets the name of the external file to read data from or write data to an XmlPort."
ms.author: solsen
ms.custom: na
ms.date: 06/15/2022
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# FileName Property
> **Version**: _Available or changed with runtime version 1.0._

Sets the name of the external file to read data from or write data to an XmlPort.

## Applies to
-   Xml Port

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Syntax

```AL
FileName = 'File.txt';
```
 
## Remarks

The **FileName** property must be set to a valid file name or a run-time error occurs.  
  
This property can be set dynamically by using the [FILENAME Method (XMLport)](../methods-auto/xmlport/xmlportinstance-filename-method.md). Using this method together with the Import method, you can create XMLports that are dynamic. This means that they can determine whether data is input or output at run time, and the name of the external file to read from or write to can also be set at run time.  
  
If **FileName** is blank, then a default request options page tab will be created, where this property can be set at run time. If no name is specified or the [UseRequestPage Property](devenv-userequestpage-property.md) is set to **false**, then a run-time error occurs.  

> [!NOTE]
> In the [!INCLUDE[webclient](../includes/webclient.md)], because web browser restrictions, the file name cannot be set. Users will have to manually select the file when the XMLport is run.
  
## See Also  

[IMPORT Method (XMLport)](../methods-auto/xmlport/xmlportinstance-import-method.md)   
[FILENAME Method (XMLport)](../methods-auto/xmlport/xmlportinstance-filename-method.md)   
[UseRequestPage Property](devenv-userequestpage-property.md)
