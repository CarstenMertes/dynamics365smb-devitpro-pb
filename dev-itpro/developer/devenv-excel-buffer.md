---
title: Exporting data to Excel using ExcelBuffer
description: Learn about the ExcelBuffer functionality and how to use it to copy data from AL to Excel.
author: kennieNP
ms.topic: how-to
ms.author: kepontop
ms.date: 03/10/2025
ms.reviewer: solsen
---

# Export data to Excel using Excel Buffer

The Excel Buffer is functionality in AL that supports creating and updating Excel workbooks from AL code. Excel Buffer isn't a native AL datatype such as an XMLPort or a JsonObject. Instead, it's a temporary table with API methods for manipulating concepts in Excel, such as worksheets, rows, and cells.

An entry in the Excel Buffer corresponds to a cell in Excel, and the table is indexed by the fields **Row No.** and **Column No.**. 

## Overall steps when working with Excel Buffer

When you work with the Excel Buffer, you typically go through the following steps:

1. Initialize the buffer (optional)
1. Add data
1. Write the Excel workbook as a temporary file
1. Consume the Excel workbook (download to the user or get as a stream)

In the following sections, you can learn more about each step and also see sample AL code that illustrates it.

## Initialize the buffer

As an Excel buffer object could potentially be reused in your code, it's considered good practice to start by initializing the buffer. This example illustrates how:

```AL
var
    TempExcelBuffer: Record "Excel Buffer" temporary;
begin
    TempExcelBuffer.Reset();
    TempExcelBuffer.DeleteAll();
```

## Add data 

You can insert data directly into the Excel Buffer or use built-in methods that can help you implement different data manipulation scenarios.

### Add data to a cell in the current worksheet

If you want to read or insert into Excel, for example, cell *C4* you simply read/create a record in the Excel Buffer with `Row No.=4`, and `Column No.=3`, and then read or assign the value to *Cell Value as Text*. 

You can also call the following method that does it all for you:

```AL
procedure EnterCell(var ExcelBuffer: Record "Excel Buffer"; RowNo: Integer; ColumnNo: Integer; Value: Variant; IsBold: Boolean; IsItalics: Boolean; IsUnderline: Boolean)
```

### Add a new row to the current worksheet

To add a new row to the current worksheet in the Excel Buffer, you can use the `NewRow` method followed by calls to the `AddColumn` method to add cells in the row. This use of the `NewRow` and `AddColumn` methods are typically used to fill in data to Excel while iterating over some table data.

```AL
var
    TempExcelBuffer: Record "Excel Buffer" temporary;
begin
    // initialize buffer code here

    TempExcelBuffer.NewRow();
    TempExcelBuffer.AddColumn('myData 1', false, '', false, false, false, '', TempExcelBuffer."Cell Type"::Text);
    TempExcelBuffer.AddColumn('myData 2', false, '', false, false, false, '', TempExcelBuffer."Cell Type"::Text);
```

The `AddColumn` method has many parameters for controlling things such as appearance (bold face, italics, or underline), number format, or data type.

## Write the Excel workbook as a temporary file 

When you're done writing data to the Excel Buffer, you can write it to an Excel workbook. The following example illustrates how:

```AL
var
    TempExcelBuffer: Record "Excel Buffer" temporary;
    WorksheetNameLbl: Label 'My Data';
begin
    // initialize buffer code here

    // code for adding data here

    TempExcelBuffer.CreateNewBook(WorksheetNameLbl);
    TempExcelBuffer.WriteSheet(WorksheetNameLbl, CompanyName, UserId);
    TempExcelBuffer.CloseBook();
```

## Consume the Excel workbook (download to the user or get as a stream)

After writing the Excel Buffer to an Excel workbook, the final step is to make it available to the user (or AL code for further processing). 

### Download the Excel workbook to the user 

To download the Excel workbook to the user, call the `OpenExcel` method as illustrated in the following example. 

```AL
var
    TempExcelBuffer: Record "Excel Buffer" temporary;
    WorksheetNameLbl: Label 'My Data';
    ExcelFileNameLbl: Label 'My Data extract';
begin
    // initialize buffer code here
    // code for adding data here
    // code for writing to Excel workbook here

    TempExcelBuffer.SetFriendlyFilename(ExcelFileNameLbl);
    TempExcelBuffer.OpenExcel();
```

### Stream the Excel workbook to further processing in AL

To stream the Excel workbook to further processing in AL, call the `OpenExcel` method as illustrated in the next example. 

```AL
var
    TempExcelBuffer: Record "Excel Buffer" temporary;
    WorksheetNameLbl: Label 'My Data';
    OutStr: OutStream;
begin
    // initialize buffer code here
    // code for adding data here
    // code for writing to Excel workbook here

    TempExcelBuffer.SaveToStream(OutStr, true);
```

## Performance impact of using Excel Buffer

When working with an instance of Excel Buffer, the full object is present in memory. This has both an impact while working with the object at runtime and also when the operating system needs to garbage collect the memory after your code has completed. 

## Online vs. on-premises usage

Some of the methods on the "Excel Buffer" table might not be available in the online version of [!INCLUDE [prod_short](../includes/prod_short.md)] as they access resources exposed there, such as direct access to the file system. These methods are marked with `[Scope('OnPrem')]` in the AL code for the "Excel Buffer" table.

## Contributors

*This article is maintained by Microsoft. Some content was originally written by the following contributors.*

* [Yun Zhu](https://www.linkedin.com/in/yzhums/) | Microsoft MVP, Dynamics 365 Business Central developer
* [Arend-Jan Kauffmann](https://www.linkedin.com/in/ajkauffmann/) | Microsoft MVP, CTO

## Related information

[Table "Excel Buffer" (Base application reference)](/dynamics365/business-central/application/base-application/table/system.io.excel-buffer)  
