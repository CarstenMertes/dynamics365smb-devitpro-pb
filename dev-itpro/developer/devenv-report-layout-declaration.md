---
title: "Report Layout Definition"
description: Report layout definitions in AL for Business Central.
ms.custom: na
ms.date: 04/03/2022
ms.reviewer: solsen
ms.topic: conceptual
author: nhsejth
---

# Report Layout Definitions

[!INCLUDE[2022_releasewave1](../includes/2022_releasewave1.md)]

When you create a new report, there are two tasks main tasks. First, you define the report dataset of data items and columns. Then, you design the report layout. You can use the [Report Object](devenv-report-object.md) and [Report Extension Object](devenv-report-ext-object.md) to define reports in AL. When you define the layout section of a report, there are two ways to do that.

1. In versions prior to [!INCLUDE[prod_short](../includes/prod_short.md)] release wave 1, layout definitions support the use of one RDL layout and one Microsoft Word layout per AL object and you then specify which report layout type is the default. we'll refer to this syntax as the *legacy layout* in this article.
2. From version [!INCLUDE[prod_short](../includes/prod_short.md)] release wave 1, the `rendering` section within the AL object allows you to specify multiple named layouts in the object and you specify the default layout by name and not by type. **Note:** The `rendering` syntax is the recommended syntax to use.

The development environment contains a code action that can convert the *legacy layout* definition into the new `rendering` section for easy update during application update. To use this code action, you must enable code actions in Visual Studio Code. For more information, see [AL Language Extension Configuration](devenv-al-extension-configuration.md).

## Rendering section

The `rendering` section consists of one or more named layout declarations.

### Layout declaration in AL 

When you declare a layout in AL, the properties [Type](properties/devenv-type-property.md) and [LayoutFile](properties/devenv-layoutfile-property.md) are mandatory, whereas the properties [Caption](properties/devenv-caption-property.md) and [Summary](properties/devenv-summary-property.md) are optional, but recommended. The application will show the translated caption and summaries to the end-user, with fallback to the layout name in case the caption is undefined. For more information, see [Defining Multiple Report Layouts](devenv-multiple-report-layouts.md).

The [MimeType](properties/devenv-mimetype-property.md) property is only supported if the `Type` is declared as `Custom`, and is a free-text string. 
It's recommended that it follows the standard naming for MIME types or is set to a path equivalent to: `Application/Report/<ExtensionName>` where `<ExtensionName>` is a short-form that identifies the owning extension. When custom-render layouts are being copied by users for customization, the MIME type follows the layout and can be verified during selection.

The syntax is as follows:

```al
layout(name)
{
    Type = RDLC | Word | Excel | Custom;
    LayoutFile = <file name>;
    Caption = <string>;
    Summary = <string>;
    MimeType = <string>;
}
```

## Sample code

### Sample code for the *legacy* layout declaration

The *legacy* layout declaration consists of three report properties as shown in the sample below. The report must specify at least one of the supported formats unless it's a *processing only* report. The sample defines both an RDLC and a Microsoft Word report layout and sets the default type to Word.

```al
report 50000 "Standard Report Layout"
{
    RDLCLayout = './StandardReportLayout.rdlc';
    WordLayout = './StandardReportLayout.docx';
    DefaultLayout = Word;
}
```

### Sample code for the new layout declaration

The new layout declaration moves the layouts to a rendering section, which must be declared just after the request page section in the report object. The default layout is specified by name using the *DefaultRenderingLayout* property. 

```al
report 50000 "Standard Report Layout"
{
    DefaultRenderingLayout = RDLCLayout;
    ...
    rendering
    {
        layout(RDLCLayout)
        {
            Type = RDLC;
            LayoutFile = './StandardReportLayout.rdlc';
            Caption = 'Standard Report Layout (RDL)';
            Summary = 'Legacy layout';
        }
        layout(WordLayout)
        {
            Type = Word;
            LayoutFile = './StandardReportLayout.docx';
            Caption = 'Standard Report Layout (Word)';
            Summary = 'Standard layout suitable for user facing documents.';
        }
    }
}
```

## See Also

[Multiple Report Layouts](devenv-multiple-report-layouts.md)
[Default Rendering Layout Property](properties/devenv-defaultrenderinglayout-property.md)
[RDLC Layout Property](properties/devenv-rdlclayout-property.md)
[Word Layout Property](properties/devenv-wordlayout-property.md)
[Default Layout](properties/devenv-defaultlayout-property.md)
