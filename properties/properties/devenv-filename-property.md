---
title: "FileName Property"
ms.date: 10/01/2020
ms.suite: na
ms.topic: article
author: jswymer
---

# FileName Property

[!INCLUDE[windows_client_only](../includes/windows_client_only.md)]

Sets the name of the external file to read data from or write data to an XMLport.  
  
## Applies to  
  
- XMLports  

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
