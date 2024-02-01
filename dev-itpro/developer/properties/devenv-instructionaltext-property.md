---
title: "InstructionalText Property"
description: "Sets the string used for instructions in the UI."
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
# InstructionalText Property
> **Version**: _Available or changed with runtime version 1.0._

Sets the string used for instructions in the UI.

## Applies to
-   Page
-   Request Page
-   Page Group

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Parameters

*Locked*  
&emsp;Type: [Boolean](../methods-auto/boolean/boolean-data-type.md)  
If `true` the InstructionalText is locked and should not be translated.  

*Comment*  
&emsp;Type: [Text](../methods-auto/text/text-data-type.md)  
Descriptive text for the InstructionalText, for example, with regards to translation.

*MaxLength*  
&emsp;Type: [Integer](../methods-auto/integer/integer-data-type.md)  
Sets the maximum length of the specific InstructionalText.

## Remarks

The default is an empty string, which means there will be no instructions. According to the user assistance model for [!INCLUDE[prod_short](../includes/prod_short.md)], apps are expected to apply instructional text to setup guides and similar pages.  

The following example illustrates how you can apply instructional text in an app:  

```AL
InstructionalText = 'Add an entity from your list of contacts. The entity can be a person or a company.';
```

Or, with the parameters:

```AL
InstructionalText = 'Add an entity from your list of contacts. The entity can be a person or a company.', Locked = true, Comment = 'Keep like this, do not translate.', MaxLength = 100;
```

## See also

[Configuring the Help Experience](../../deployment/configure-help.md)  
[Page object](../devenv-page-object.md)  
