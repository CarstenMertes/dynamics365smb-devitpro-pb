---
title: Creating an Excel layout report
description: Learn how to create a report using an Excel layout.
author: SusanneWindfeldPedersen
ms.custom: bap-template
ms.date: 03/12/2025
ms.reviewer: jswymer
ms.topic: conceptual
ms.author: kepontop
---
# Creating an Excel layout report

[!INCLUDE[2022_releasewave1](../includes/2022_releasewave1.md)]

When you create a new report, there are two main tasks to consider. First, you define the report dataset of data items and columns. Then, you design the report layout. With the Excel report layout, you can create a basic report that prints a dataset and leaves it up to the end-user to further modify it by using the full palette of capabilities in Excel such as sliders, diagrams, charts, pivot tables, and PowerQuery to design the report. This offers flexibility and freedom for the end-user, being able to change the look and feel of a report, adding more views, filtering, and sorting on data. Such a layout designed by the end-user can be imported and used as a new layout. 

For more information about the report object, go to [Report Object](devenv-report-object.md) and for report extension objects, go to [Report Extension Object](devenv-report-ext-object.md).

## How Excel layouts work

When designing an Excel layout, you need to know the following information:

- How the layout is connected to the dataset definition, also known as the _data contract_.
- How the layout file is validated when importing it into [!INCLUDE[prod_short](../includes/prod_short.md)].
- How the [!INCLUDE[prod_short](../includes/prod_short.md)] server merges the layout with data when running the report.

### Excel layout data contract in 2023 release wave 1 and earlier versions

Every Excel layout file must have a worksheet called _Data_. This worksheet has one purpose: defining which metadata fields from the the dataset definition of the report object the layout uses, which is sometimes also called the _data contract_ between the layout file and the report dataset definition. The data contract consists of the following rules:

1. Metadata fields must be written in the first row of the _Data_ worksheet, one in each cell.
1. All metadata fields in the _Data_ worksheet must exist as metadata fields in the dataset definition of the report object.
1. You can't rename fields in the _Data_ worksheet. They must match metadata fields in the dataset definition.
1. You don't have to use all metadata fields in the dataset definition in the _Data_ worksheet.

> [!TIP]  
> When developing Excel layouts, you can add demo data to the _Data_ worksheet to make it easier to see the end result when the report is rendered with the layout. The data is removed when importing it to [!INCLUDE[prod_short](../includes/prod_short.md)] but if you include Excel layouts in an app/extension, you might want to keep the demo data there for easier troubleshooting later.

For more information about the data contract, go to [Understanding Excel layouts](/dynamics365/business-central/ui-excel-report-layouts?tabs=any-report#understanding-excel-layouts).

### Excel layout data contract in 2023 release wave 2 and later versions

[!INCLUDE[2023_releasewave2](../includes/2023_releasewave2.md)]

The [ExcelLayoutMultipleDataSheets property](properties/devenv-excellayoutmultipledatasheets-property.md) allows you to work with reports that render multiple worksheets for the report data when the dataset has multiple data items. By setting the property to `true`, the AL runtime generates an Excel worksheet for each data item and places its data there. Otherwise, if the property is `false`, which is the default, a single sheet is used for all data (as described in the previous section).

Each of the multiple sheets is named #DataItemName, where DataItemName is the name given to the dataitem in the report design. When new empty Excel layouts are added to the report, the property is used to determine the sheet structure.

With data in multiple worksheets, the report layout can now easily include data models defined with the PowerPivot feature in Excel.

### System Excel sheets

[!INCLUDE[2023_releasewave2](../includes/2023_releasewave2.md)]

Starting from version 23.3, the [!INCLUDE[prod_short](../includes/prod_short.md)] server adds three system worksheets that you can use for easier layouts and for creating translatable Excel layouts:

- TranslationData
- CaptionData
- Aggregated Metadata

All three system worksheets are hidden by default and the data in these worksheets is organized in Excel tables from which you can reference individual fields using Excel table formulas.

> [!NOTE]  
> Excel report layout workbooks include named formulas for easier lookups. For more information, go to [Named formulas](#named-formulas).

#### TranslationData worksheet definition (table TranslationData)

The *TranslationData* worksheet contains data that you can use in your layouts to provide multi-language strings that don't exist as captions in the report object. When the [!INCLUDE[prod_short](../includes/prod_short.md)] server generates the Excel report, it can use data from the *TranslationData* table as part of translating strings to the user's language.

The data in the *TranslationData* worksheet is located in the Excel table **TranslationData** with three columns **CaptionKey**, **Language, and **Value**: 

|Column|Description|
|------|-----------|
|CaptionKey| A unique name that can be used in the layout enclosed in $ characters. Read more about how translations work in the following section.|
|Language| The language of the string, such as `en-US` or `da-DK`.|
|Value| The string in the language specified by the Language column.|

#### CaptionData worksheet definition (table CaptionData)

The *CaptionData* worksheet contains data from column captions and report labels specified in the AL report object. When the [!INCLUDE[prod_short](../includes/prod_short.md)] server generates the Excel report, it can use data from the **CaptionData** table as part of translating strings to the users language.

Column captions are generated for all dataset fields with 'IncludeCaption = true'.

The data in the *CaptionData* worksheet is located in the Excel table **CaptionData** with two columns **CaptionKey** and **Value**: 

|Column|Description|
|------|-----------|
|CaptionKey| Includes field caption names for all dataset fields with 'IncludeCaption = true' and label names in the labels section of the report. Values from the CaptionKey column can be used in the layout enclosed in $ characters. Read more about how translations work in the following sections.|
|Value| The string in the language specified by the user when running the report. Data in this column is inserted by the [!INCLUDE[prod_short](../includes/prod_short.md)] server when it generates the Excel report. Don't add data here manually.|

#### Aggregated metadata sheet definition (multiple tables)

The *Aggregated metadata* worksheet contains data from the report AL metadata, request metadata, request page options, and filters. Each type of data is available in its own Excel table:

- ReportMetadataValues
- ReportRequestValues
- ReportRequestPageValues
- ReportFilterValues

##### ReportMetadataValues table

The *ReportMetadataValues* table contains metadata from the report object.

| Column Key              | Description |
|----------------------- | ----------- |
|Extension ID | The unique ID (GUID) of the app/extension for the report. |
|Extension Name | The name of the app/extension for the report. |
|Extension Publisher | The name of the publisher of the app/extension for the report. |
|Extension Version | The version of the app/extension for the report.|
|Object ID | The object ID of the report. |
|Object Name | The object name of the report.|
|About This Report Title | The *about this report title* as declared in the Request Page setup in the AL report. |
|About This Report Text | The *about this report text* as declared in the Request Page setup in the AL report. |
|Report help link | Help link (if setup) in the extension and report object.|

##### ReportRequestValues table

The *ReportRequestValues* table contains metadata from the report request (the report invocation that created the document).

| Column Key              | Description |
|----------------------- | ----------- |
| Tenant Id | Contains the Entra/AAD tenant ID of the environment. |
| Environment name | The name of the environment. Might be empty for on-premises installations. |
| Environment type | The environment type (Production or sandbox). Might be empty for on-premises installations. |
| Company name | The company name that the user was operating in when running the report. |
| Company Id | The Company ID (GUID). |
| User name | The user who ran the report. |
| User Id | The user ID associated to 'User name'. |
| Date | The date and time of the report invocation. |
| Language | The application language identified (LCID, Windows language identifier).|
| Format Region | The Format Region applied to the report (specified as a culture tag such as 'en-US' or 'da-DK'). |

##### ReportRequestPageValues table

The *ReportRequestPageValues* table contains metadata from the report request page when the report request was issued.

The table has two columns **Request Page Option** and **Request Page Option Value**. It contains all Key-Value pairs of entries from request page options.

##### ReportFilterValues table

The *ReportFilterValues* table contains metadata from the report request page when the report request was issued.

The table has two columns **Filter** and **Filter Value**. It contains all Key-Value pairs of filters from the request page.

The actual filter format is '\<DataItemName\>::\<Source Table Caption\>::\<FilterGroup\>::\<Field Caption\>'. 

There is one row for each active filter defined on the request page.


#### Named formulas 

In Business Central 2024 release wave 2 and later, when you create Excel report layout workbooks, either from VSCode or when you get a new template from the request page, Excel report layout workbooks include named formulas for easier lookups. Instead of having to write complicated VLOOKUP or XLOOKUP formulas, report authors can use named formulas, such as **ReportRequest.Date** or **ReportMetaData.ReportHelpLink**.

To see all available formulas in an Excel workbook, in the **Defined Names** group, choose **Formulas**, and then **Name Manager**.

### Translating Excel sheets in 2023 release wave 2 and later versions

[!INCLUDE[2023_releasewave2](../includes/2023_releasewave2.md)]

Starting in version 23.3, you can create Excel layouts that work for multiple languages. 

There are two ways to translate strings:

- Using report captions and labels or per-layout translation texts with Excel lookup functions.
- Using '\$tag\$' substitution.

If strings are available in field captions or labels in the report object, you can use Excel cell lookups to the data in the **CaptionData** table. This table populates by the [!INCLUDE[prod_short](../includes/prod_short.md)] server when the report is generated and contains the caption strings for fields and report labels from the report object. Use the same technique with the **TranslationData** table that holds per-layout translation texts. For these texts, use the *Format Region* field from the **ReportRequestValues** table in your Excel lookups.

It's also possible to use '\$tag\$' substitution for Excel elements in your worksheets. At report generation time, the [!INCLUDE[prod_short](../includes/prod_short.md)] server replaces '\$tag\$' with the corresponding value defined in the **TranslationData** or **CaptionData** tables. If a tag exists in both tables, data from the **TranslationData** table takes precedence. The tag name is case-sensitive and unmatched elements are left unmodified.

The following Excel elements can be translated:

- Worksheet name
- Text data in a cell
- Chart title
- Chart axis titles (available from version 24.1)
- Pivot table name (right-click on the pivot table, choose **PivotTable Options**, then add your tag in the **PivotTable Name** field)
- Pivot field name (right-click on the field in the pivot table, choose **Field Settings**, then add your tag in the **Custom Name** field)
- Slicer name (right-click on the slicer, choose **Slicer Settings**, then add your tag in the **Caption** field)

Worksheet references with translation tags are updated in cell formulas as well to maintain proper data references in the final document.

### Validating an Excel layout

When importing an Excel layout as part of an app or when a user uploads an Excel layout file, [!INCLUDE[server](includes/server.md)] does the following operations:
 
1. Loads the Excel layout file and validates whether the file is indeed an Excel file (.xlsx) and that it isn't password protected. If the file isn't a valid Excel file, [!INCLUDE[server](includes/server.md)] rejects the layout.
1. Reads the metadata fields present in the *Data* worksheet (the content of the data contract). If no _Data_ worksheet exists, [!INCLUDE[server](includes/server.md)] rejects the layout.
1. Removes any other data present in the *Data* worksheet.
1. Validates whether the metadata fields present in the *Data* worksheet are all present as metadata fields in the dataset definition of the report object. In other words, [!INCLUDE[server](includes/server.md)] checks that the data contract is valid. If it isn't, [!INCLUDE[server](includes/server.md)] rejects the layout.

### Running a report with an Excel layout

When a report with an Excel layout is run, [!INCLUDE[server](includes/server.md)] does the following operations:

1. Generates the dataset as specified in the dataset definition in the report object and modified by the filters and options from the request page.
1. Loads the Excel layout file.
1. Inserts the data into the *Data* table in the *Data* worksheet in the Excel layout file.
1. Provides the merged Excel workbook to the user for download or view in Excel online if enabled by the tenant administrator. For more information about viewing Excel outputs in Excel online, visit [Save Excel workbooks and report files in OneDrive](/dynamics365/business-central/across-onedrive-overview#save-excel-workbooks-and-report-files-in-onedrive).

### Changing the data contract after adding new columns to the report dataset

If you add new columns to the report dataset after creating Excel layouts, the data contracts in the layouts don't get updated automatically. But you don't need to recreate the layouts from scratch, you can add the new columns manually to the header line in the data contract worksheets.

For a report developer working with AL code, maybe the simplest way to get the new column names is from the AL code for the report object. For a report developer working just in Excel, the simplest way to get the new column names is to run the report in [!INCLUDE[prod_short](../includes/prod_short.md)] and on the request page, then choose the **Microsoft Excel Document (data only)** option. This gives you an Excel workbook with all the columns in the data contract.

## Report labels in Excel layouts

Report labels are used by report layouts as, for example, the heading for a field in a table, the title for a chart, or the title for the report itself. 

Starting in version 23.3, report labels defined in the *Labels* section of the report object and captions included on dataitem columns using the [IncludeCaption property](properties/devenv-includecaption-property.md) are available in the `CaptionData` worksheet in Excel. 

For more information about labels, go to [Report labels](./devenv-report-object.md#report-labels).

## Formatting data in Excel layouts

[!INCLUDE[formatting_data_in_layouts](../includes/include-formatting-data-in-layouts.md)]

Specifically for Excel layouts, there are many ways to control formatting of data elements directly in Excel. For more examples on how to format data in Excel, go to:

- [Formatting dates in Excel](https://support.microsoft.com/en-us/office/format-a-date-the-way-you-want-8e10019e-d5d8-47a1-ba95-db95123d273e)
- [Formatting numbers in Excel](https://support.microsoft.com/en-us/office/number-format-codes-5026bbd6-04bc-48cd-bf33-80f18b4eae68)

## Drillthrough to Business Central from an Excel layout

With drillthrough in an Excel layout, you can create hyperlinks back into [!INCLUDE[prod_short](../includes/prod_short.md)] from Excel cells. When the report user selects the cell, they drillthrough to the target page to get details that are filtered to that context. To implement a drillthrough link, you need to know, which page to open and also construct, which filters to apply to that page. You filter the data that is displayed in the page by using the filter URL parameter. The filter parameter lets you display specific records from the underlying table of the page.

For more information, go to [Web URL syntax](devenv-web-client-urls.md).

## Using fonts in Excel layouts

[!INCLUDE[using_fonts](../includes/include-excel-word-layouts-fonts.md)]

## Using Office document themes in Excel layouts

[!INCLUDE[using_office_themes](../includes/include-excel-word-layouts-themes.md)]

## Best practices for Excel layouts

### Excel functionality

When doing lookups inside the Excel workbook, use the `XLOOKUP` function instead of `VLOOKUP`. For more information, go to [XLOOKUP function](https://support.microsoft.com/office/xlookup-function-b7fd680e-6d10-43e6-84f9-88eae8bf5929).

Consider using Power Query as a powerful tool to clean and transform data (for example, use it to set the correct data types). Power Query is available in all Excel versions since Excel 2016. The connectors offered by Excel versions differs as stated in this support article: [Power Query data sources in Excel versions](https://support.microsoft.com/office/power-query-data-sources-in-excel-versions-e9332067-8e49-46fc-97ff-f2e1bfa0cb16). For more information, go to [Power Query in Excel](https://powerquery.microsoft.com/excel). 

Table formulas in Excel are a powerful way to work on table data. For more information, go to [Use calculated columns in an Excel table](https://support.microsoft.com/office/use-calculated-columns-in-an-excel-table-873fbac6-7110-4300-8f6f-aafa2ea11ce8#:~:text=As%20a%20result%2C%20Excel%20built%20the%20formula%3A%20%3DSUM,to%20use%20the%20same%20formula%20for%20each%20row).

### Worksheet naming and location

Arrange worksheets in the order you think are most useful for users so that they don't have to scroll when using the report.

Good worksheet names help users quickly get an overview of the information they can obtain by navigating to the worksheet.

An Excel worksheet can be up to 31 characters long.

### One or multiple worksheets?

In contrast to a report designed for print or pdf, an Excel report typically consists of multiple worksheets, each of which is designed for a different purpose. Some common types of worksheets are:

- Overview dashboard
- Pivot table
- Table
- Print-friendly
- About the report

There's no technical limit to the number of worksheets in a report, but users probably prefer limited number of worksheets. You can develop multiple Excel layouts for the same report, so maybe design for a specific persona.

#### Overview dashboard worksheet

Excel has visuals such as charts and maps, sparklines, and slicers, that can be used for creating dashboards known from Business Intelligence products such as Power BI. You can use these visuals to create dashboard worksheets that let users interact with the data and get visually appealing graphs showing trends or top 10 numbers.

#### Pivot table worksheet

Use a pivot table worksheet to give users a way to interact with the dataset. Typically, only one pivot worksheet in the report is needed (unless you want to offer different ready-made analysis). If you add multiple ready-made pivot table worksheets, consider naming them *X by Y*, such as *Customers by Item* or *Sales by Region*.

#### Table worksheet

A table worksheet can be used to display a specific view on the dataset, maybe only showing a subset of the columns and maybe even with some added computed columns. 

#### Print-friendly worksheet

Some users might want to print the report, but this shouldn't force you to design all worksheets to be print-friendly. Instead, consider having one or more worksheets that are optimized for print, maybe one for horizontal and one for landscape paper orientation.

#### About the report worksheet

Users aren't always 100% sure how your report is used and for whom it was designed. Consider always having an *About the report* worksheet that explains:

- What the report is about and maybe also for which persona.
- A description for each worksheet that explains what the users can do here.
- Maybe also add *See also* links to documentation in case the user wants to learn more.

## Example: Create a simple Excel layout report

The following steps show how to create a basic report based on an Excel layout. The example also illustrates how compilation triggers a starter template for the Excel layout. If an existing layout is referenced with the `LayoutFile` property, the layout is validated based on the schema of the report dataset.

The example extends the **Contact List** report only by adding a `rendering` section, which adds a new Excel layout to the list of options for printing the **Contact List** report. The layout doesn't yet exist, but is generated based on the *existing report dataset* for the report and then be modeled by using Excel reporting capabilities. The example uses the [Type Property](properties/devenv-type-property.md) to set the type of report to `Excel` and it uses the [LayoutFile Property](properties/devenv-layoutfile-property.md) to specify the name of the file that contains the Excel layout. If LayoutFile property isn't present, it is generated.

1. Create a new report extension of the **Contact List** page by adding the following lines of code:

    ```al
    reportextension 50101 MyExtContactList extends "Contact - List"
    {
        rendering
        {
            layout(LayoutExcel)
            {
                Type = Excel;
                LayoutFile = 'MyExcelContactList.xlsx';
            }
        }
    }
    ```

1. Now, select <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>, and then choose **AL: Package**. The `MyExcelContactList.xlsx` is generated, as you can see in the right pane of Visual Studio Code.
  
    > [!TIP]  
    > Another way of generating the data set to build a layout on, is to run a report in Business Central and on the request page, then choose the **Microsoft Excel Document (data only)** option, and you'll get the same starting point. Then you can design the layout, save as a new layout, and include in your AL project.
1. Right-click the generated `MyExcelContactList.xlsx` file, and choose **Reveal in File Explorer**. This step opens File Explorer.
1. Choose the `MyExcelContactList.xlsx` file in File Explorer and open it in Excel.  
Excel now opens and you should see the dataset of the Contact List. **Note** that it's important to not change the dataset in Excel, only the layout.
1. In Excel, go to the **Insert** tab, choose **PivotTable**, and then choose **From Table/Range** with the default options of **Data** and **New worksheet**. Choose the **OK** button.
1. From the **PivotTable Fields** pane to the right, choose a suitable number of fields to add to the report.
1. Save the report and close the Excel window.
1. Back in Visual Studio Code, select <kbd>Ctrl</kbd>+<kbd>F5</kbd>  to compile and launch [!INCLUDE [prod_short](includes/prod_short.md)].  
1. Now, to choose the changed report layout, search for the **Report Layout Selection** page, and then search for the **Contact List** (ID 5050) report.
1. In the **Layout Type** column, choose **Excel**, and then choose the **Run Report** from the action bar.
1. On the request page, choose the **Download** button, and once the report is downloaded, open it.
1. In Excel, you should now see the Contact List report as a pivot table, sorted as you specified in step 6.

> [!NOTE]  
> If the report layout isn't generated, open the `settings.json` file from Visual Studio Code. Use **Ctrl+Shift+P**, then choose **Preferences: Open User Settings**, locate the **AL Language extension**. Under **Compilation Options**, choose **Edit in settings.json** and add the following line:  
>
>```json
>"al.compilationOptions": {
>   "generateReportLayout": true
> }
>```

It's possible to specify multiple layouts for a report. For more information, go to [Defining Multiple Report Layouts](devenv-multiple-report-layouts.md).

## Related information

[Report Design Overview](devenv-report-design-overview.md)  
[Report Object](devenv-report-object.md)
[Creating a Word Layout Report](devenv-howto-report-layout.md)  
[Creating an RDL Layout Report](devenv-howto-rdl-report-layout.md)  
[Defining Multiple Report Layouts](devenv-multiple-report-layouts.md)  
[ExcelLayout Property](properties/devenv-excellayout-property.md)  
[ExcelLayoutMultipleDataSheets Property](properties/devenv-ExcelLayoutMultipleDataSheets-property.md)   
[LayoutFile Property](properties/devenv-layoutfile-property.md)  
[Save Excel workbooks and report files in OneDrive](/dynamics365/business-central/across-onedrive-overview#save-excel-workbooks-and-report-files-in-onedrive)  
[Understanding Excel layouts](/dynamics365/business-central/ui-excel-report-layouts?tabs=any-report#understanding-excel-layouts)  
[Available Fonts in Business Central online](/dynamics365/business-central/ui-fonts)  
