---
title: "Caption Property"
description: "Sets the string that is used to identify a control or other object in the user interface."
ms.author: solsen
ms.custom: na
ms.date: 10/25/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Caption Property
> **Version**: _Available or changed with runtime version 1.0._

Sets the string that is used to identify a control or other object in the user interface.

## Applies to
-   Table
-   Table Field
-   Page Field
-   Field Group
-   Page
-   Request Page
-   Page Label
-   Page Group
-   Page Part
-   Page System Part
-   Page Action
-   Page Action Separator
-   Page Action Group
-   Xml Port
-   Report
-   Query
-   Query Column
-   Query Filter
-   Report Column
-   Enum Value
-   Page Custom Action
-   Page System Action
-   Page View
-   Report Layout
-   Profile
-   Enum Type
-   Permission Set

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Parameters
The property has three optional parameters; `Locked`, `Comment`, and `MaxLength`.

*Locked*  
&emsp;Type: [Boolean](../methods-auto/boolean/boolean-data-type.md)  
If `true` the Caption is locked and should not be translated.  

*Comment*  
&emsp;Type: [Text](../methods-auto/text/text-data-type.md)  
Descriptive text for the Caption, for example, with regards to translation.

*MaxLength*  
&emsp;Type: [Integer](../methods-auto/integer/integer-data-type.md)  
Sets the maximum length of the specific Caption.

## Syntax
```AL
Caption = 'Name';
```

Or, with parameters:

```AL
Caption = 'Name', Locked = true, Comment = 'Keep like this, do not translate.', MaxLength = 20;
```

## Remarks

A caption is the text used to show the identity of a control. For example, in the caption bar of a page or a label for another control.  

> [!NOTE]  
> For query columns, when you run the query from Object Designer, the About This Query window that opens in the [!INCLUDE[rtc](../includes/rtc_md.md)] displays the value for the [Name Property](./devenv-properties.md) of the query column, not the Caption property or CaptionML Property.  

## See Also

[ShowCaption Property](devenv-showcaption-property.md)  
[Working with Translation Files](../devenv-work-with-translation-files.md)