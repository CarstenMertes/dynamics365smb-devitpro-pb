---
title: Report extension object
description: The report extension object in AL for Business Central allows you to create an extension of an existing report.
author: SusanneWindfeldPedersen
ms.custom: na
ms.date: 12/01/2023
ms.reviewer: na
ms.topic: article
ms.author: solsen
---

# Report extension object

[!INCLUDE [2021_releasewave1](../includes/2021_releasewave1.md)]

With the report extension object, you can extend existing report objects, similar to how you extend tables and pages. With report extensions, you can extend an existing report by:

- Adding columns to existing data items in the report dataset
- Adding new data items
- Adding trigger implementations
- Adding to request pages
- Adding more report layouts, either to reflect new fields that are added with an extension, or simply adding new report layouts on an existing report dataset.

For a report to be extended, the `Extensible` property must be set to `true`, which is the default value. The value `true`, which means that reports by default can be extended, unless they explicitly have the `Extensible` property set to `false`. For more information, see [Extensible Property](properties/devenv-extensible-property.md).

> [!NOTE]  
> Extension objects can have a name with a maximum length of 30 characters.

## Report extension layout

From [!INCLUDE [prod_short](../includes/prod_short.md)] 2022 release wave 1, report extensions can have one or more layouts defined. For more information, see [Defining Multiple Report Layouts](devenv-multiple-report-layouts.md). The report layout of an existing report can't be extended, but new layouts can be added. To use an existing report as a starting point, you can download the layout from [!INCLUDE [prod_short](../includes/prod_short.md)] and include it in the extension project. 

Layouts that are included in a report extension shows up in [!INCLUDE [prod_short](../includes/prod_short.md)] as more layouts to the report. Layout from a report extension are **not automatically** used when the extension is deployed. To use one of the new report layouts, go to the **Report Layouts** page in [!INCLUDE [prod_short](../includes/prod_short.md)], and then choose the layout for the report in question as the new **Default Layout**.

## Snippet support

Typing the shortcut `treportext` creates the basic layout for a report extension object when using the [!INCLUDE[d365al_ext_md](../includes/d365al_ext_md.md)] in Visual Studio Code.

[!INCLUDE[intelli_shortcut](includes/intelli_shortcut.md)]

## Report extension example

The following example illustrates a simplified table extension, which adds a new field to the `Customer` table, `MyField`. The report extension `MyExtension` then adds `MyField` and an extra field in original `Customer` table to the **Customer - Top 10 List** report, and it adds a new Excel layout to the report. The example also illustrates how a new field added to the report extension, can be modified using the `OnBeforeAfterGetRecord` trigger. For more information, see [OnBeforeAfterGetRecord (Report Extension Data Set Modify) Trigger](triggers-auto/reportextensiondatasetmodify/devenv-onbeforepredataitem-reportextensiondatasetmodify-trigger.md). For a list of triggers that can be used inside the `modify` section of a report, go to the [See Also](devenv-report-ext-object.md#see-also) section.

For a more advanced example, see [Report Extension Example](devenv-report-ext-example.md). 

> [!NOTE]  
> Inside the `requestpage` element, you cannot modify any properties.
>
> Using the `OnInitReport` trigger is not supported for report extensions. The `OnPreReport` and `OnPostReport` triggers are run after the original report's equivalent triggers.

```AL
tableextension 50110 CustomerTableExt extends Customer
{
    fields
    {
        field(50100; MyField; Integer)
        {
            DataClassification = ToBeClassified;

        }
    }
}

reportextension 50110 MyExtension extends "Customer - Top 10 List"
{
    dataset
    {
        add(Integer)
        {
            // add existing field from base table to dataset
            column(fromBaseTable; Customer.GLN) { }
            // add field from table extending Customer
            column(fromBaseTableExt; Customer.MyField) { }
        }

        add(Customer)
        {
            // add a new field to the dataset
            column(netWeight; netWeight) { }
        }

        modify(Customer)
        {
            // modify the new, added field
            trigger OnBeforeAfterGetRecord()
            begin
                if (weightInPounds) then begin
                    netWeight := netWeight * 2.2;
                end else begin
                    netWeight := netWeight;
                end;
            end;
        }
    }

    requestpage
    {
        layout
        {
            addafter(Show)
            {
                // add field from table extension to request page
                field(fromBaseTableExt; Customer.myField) { }
            }
        }
    }

    // add additional report layouts to the report
    rendering
    {
        layout(MyExcelLayout)
        {
            Type = Excel;
            Caption = 'Top 10 customers (Excel)';
            Summary = 'Top 10 customers in my favorite analysis app: Excel';
            LayoutFile = 'Top10CustomersAsExcel.xlsx';
        }
    }

    trigger OnPreReport()
    begin
        // add code to run before the report is run, will be run after the original report's equivalent trigger
    end;

    trigger OnPostReport()
    begin
        // add code to run after the report is run, will be run after the original report's equivalent trigger
    end;

    var
        netWeight: Integer;
        weightInPounds: Boolean;

}
```

[!INCLUDE [send-report-excel](includes/send-report-excel.md)]

## See Also

[Report Extension Example](devenv-report-ext-example.md)  
[Using request pages with reports](devenv-request-pages-for-reports.md)   
[Creating an Excel layout report](devenv-howto-excel-report-layout.md)   
[Creating an RDL Layout Report](devenv-howto-rdl-report-layout.md)  
[Creating a Word Layout Report](devenv-howto-report-layout.md)  
[Adding Help Links from Pages, Reports, and XMLports](devenv-adding-help-links-from-pages-tables-xmlports.md)  
[Page Extension Object](devenv-page-ext-object.md)  
[Page Properties](properties/devenv-page-property-overview.md)  
[Developing Extensions](devenv-dev-overview.md)  
[AL Development Environment](devenv-reference-overview.md)  

Report extension triggers  
[OnPostReport (Report Extension) Trigger](triggers-auto/reportextension/devenv-onpostreport-reportextension-trigger.md)  
[OnPreReport (Report Extension) Trigger](triggers-auto/reportextension/devenv-onprereport-reportextension-trigger.md)  
[OnAfterAfterGetRecord (Report Extension Data Set Modify) Trigger](triggers-auto/reportextensiondatasetmodify/devenv-onafteraftergetrecord-reportextensiondatasetmodify-trigger.md)  
[OnAfterPostDataItem (Report Extension Data Set Modify) Trigger](triggers-auto/reportextensiondatasetmodify/devenv-onafterpostdataitem-reportextensiondatasetmodify-trigger.md)  
[OnAfterPreDataItem (Report Extension Data Set Modify) Trigger](triggers-auto/reportextensiondatasetmodify/devenv-onafterpredataitem-reportextensiondatasetmodify-trigger.md)  
[OnBeforeAfterGetRecord (Report Extension Data Set Modify) Trigger](triggers-auto/reportextensiondatasetmodify/devenv-onbeforeaftergetrecord-reportextensiondatasetmodify-trigger.md)  
[OnBeforePostDataItem (Report Extension Data Set Modify) Trigger](triggers-auto/reportextensiondatasetmodify/devenv-onbeforepostdataitem-reportextensiondatasetmodify-trigger.md)  
[OnBeforePreDataItem (Report Extension Data Set Modify) Trigger](triggers-auto/reportextensiondatasetmodify/devenv-onbeforepredataitem-reportextensiondatasetmodify-trigger.md)