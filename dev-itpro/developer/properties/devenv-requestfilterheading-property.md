---
title: "RequestFilterHeading Property"
description: "Sets a caption for the request page tab that is related to this data item."
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
# RequestFilterHeading Property
> **Version**: _Available or changed with runtime version 1.0._

Sets a caption for the request page tab that is related to this data item. The value is taken from the RequestFilterHeadingML Property if this property is set.

## Applies to
-   Xml Port Table Element
-   Report Data Item

[//]: # (IMPORTANT: END>DO_NOT_EDIT)


## Parameters

*Locked*  
&emsp;Type: [Boolean](../methods-auto/boolean/boolean-data-type.md)  
If `true` the RequestFilterHeading is locked and should not be translated.  

*Comment*  
&emsp;Type: [Text](../methods-auto/text/text-data-type.md)  
Descriptive text for the RequestFilterHeading, for example, with regards to translation.

*MaxLength*  
&emsp;Type: [Integer](../methods-auto/integer/integer-data-type.md)  
Sets the maximum length of the specific RequestFilterHeading.

## Property Value  

Any valid string. If [RequestFilterHeadingML Property](devenv-requestfilterheadingml-property.md) is set, then the value for the selected language is used. If [RequestFilterHeadingML Property](devenv-requestfilterheadingml-property.md) is not set, then the default is the name of the table that is the specified in the [DataItemTable Property](./devenv-properties.md) in a report or in the [SourceTable (XMLports) Property](./devenv-properties.md) in an XMLport. 

## Syntax

```AL
RequestFilterHeading = 'Entry';
```

Or, with parameters:

```AL
RequestFilterHeading = 'Entry', Locked = true, Comment = 'Keep like this, do not translate.', MaxLength = 20;
```
   
## See Also

[Request Pages](../devenv-request-pages.md)  
[Working with Translation Files](../devenv-work-with-translation-files.md)