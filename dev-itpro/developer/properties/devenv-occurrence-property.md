---
title: "Occurrence Property"
description: "Sets a value that specifies whether an attribute must occur in the data that is being imported or exported."
ms.author: solsen
ms.custom: na
ms.date: 12/08/2022
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Occurrence Property
> **Version**: _Available or changed with runtime version 1.0._

Sets a value that specifies whether an attribute must occur in the data that is being imported or exported.

## Applies to
-   Xml Port Field Attribute
-   Xml Port Text Attribute

## Property Value

|Value|Available or changed with|Description|
|-----------|-----------|---------------------------------------|
|**Required**|runtime version 1.0|If the attribute must be part of the data. This is the default value.|
|**Optional**|runtime version 1.0|If the attribute does not have to be part of the data.|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)


## Syntax

```AL
Occurrence = Optional;
```
  
## Remarks  

This property is primarily used to ensure that the XML data that you are importing conforms to the data structure in [!INCLUDE[d365fin_long_md](../includes/d365fin_long_md.md)].  
  
## See Also  
[Get Started with AL](../devenv-get-started.md)  
[Developing Extensions](../devenv-dev-overview.md)  