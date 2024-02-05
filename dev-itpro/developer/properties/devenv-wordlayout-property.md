---
title: "WordLayout Property"
description: "Sets the Word layout that is used on a report and returns it as a data stream."
ms.author: solsen
ms.custom: na
ms.date: 10/11/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# WordLayout Property
> **Version**: _Available or changed with runtime version 1.0._

Sets the Word layout that is used on a report and returns it as a data stream.

## Applies to
-   Report
-   Report Extension

[//]: # (IMPORTANT: END>DO_NOT_EDIT)


[!INCLUDE[possible_layouts_note](../includes/include-possible-layouts-note.md)]

## Remarks

The Word file must be in the same folder as the AL object.

[!INCLUDE[single_layouts](../includes/include-single-layout-obsolete.md)]

## Example

The following example shows how to use this property to generate the *MyWordReport.docx* file.

```AL
pageextension 50100 MyExtension extends "Customer List"
{
    trigger OnOpenPage();
    begin
        report.Run(Report::MyWordReport);
    end;
}

report 50124 MyWordReport
{
    DefaultLayout = Word;
    WordLayout = 'MyWordReport.docx';
}
```

## See also

[Creating a Word Layout Report](../devenv-howto-report-layout.md)  
[RDLCLayout Property](devenv-rdlclayout-property.md)  
[Creating an RDL Layout Report](../devenv-howto-rdl-report-layout.md)  