---
title: Test reports
description: How to validate if a report produces correct data
author: SusanneWindfeldPedersen
ms.reviewer: solsen
ms.topic: conceptual
ms.author: solsen
ms.date: 04/01/2021
---

# Test reports

Testing your report requires you to run it and to verify the data output. This practice helps you ensure that your customers are presented with complete and accurate data.  

Before extensions, the output of a report was saved to a file, but extensions deployed to [!INCLUDE[d365fin_long_md](includes/d365fin_long_md.md)] can't access the file system and therefore must save the output of a report to a stream. Codeunit 131007 `Library - Report Dataset` offers a high-level API for running and testing the output of reports that doesn't require direct access to the file system.

## Example

The following example shows how to initialize the codeunit 131007 `Library - Report Dataset` by using the `RunReportAndLoad` method. This method is preferred as it runs the report and initialize the `Library - Report DataSet` codeunit. To verify the output, call either the `AssertElementWithValueExists` or the `AssertElementWithValueNotExist` method. The other methods in the library should work as well if they don't contain “Tag” in the name. `RUNREQUESTPAGE` and `[RequestPageHandler]` are optional and you can use them when you want to open the request page. 

> [!TIP]  
> If you want to run the report separately and load the data from the input stream manually, you can use the `LoadDataFromInstream` method.

```AL
codeunit 50105 MyReportTesting
{
    Subtype = Test;
    
    [Test]
    [HandlerFunctions('RemittanceAdviceJournalRequestPageHandler')]
    procedure TestingReports()
    var
        XmlParameters: Text;
        LibraryReportDataset: Codeunit "Library - Report Dataset";
        GenJournalLine: Record "Gen. Journal Line";
    begin
        // Run the Report Remittance Advice - Journal. 
        XmlParameters := Report.RunRequestPage(Report::"Remittance Advice - Journal");
        LibraryReportDataset.RunReportAndLoad(Report::"Remittance Advice - Journal", GenJournalLine, XmlParameters);

        // Verifying Total Amount on Report. 
        LibraryReportDataset.AssertElementWithValueExists('Amt_GenJournalLine', GenJournalLine.Amount);
    end;

    [RequestPageHandler]
    procedure RemittanceAdviceJournalRequestPageHandler(var RemittanceAdviceJournal: TestRequestPage 399)
    begin
        // Empty handler used to close the request page. We use default settings. 
    end;
}
```

Any changes done in the handler above results in the `XmlParameters` being changed and applied automatically when the report runs. Examples of the implementation in the existing tests are in `Codeunit 133770` and `Codeunit 134141`.

## Remarks

[TestRequestPage.SaveAsXML](methods-auto/testrequestpage/testrequestpage-saveasxml-method.md) uses a different format than [Report.SaveAsXML](methods-auto/report/report-saveasxml-method.md) or [Report.SaveAs](methods-auto/report/report-saveas-method.md) by serializing the output of **Report Previewer**. This is a component that will be deprecated in the future and replaced with the new methods that can be used for the new tests. Another difference is that `TestRequestPage.SaveAsXML` requires files to be saved to disk and loaded, while other methods work in memory, making them more efficient. 

> [!NOTE]  
> The existing tests still need support and the codeunit solves this problem by supporting both formats for now. `TestRequestPage.SaveAsXML` uses Tags for values, while the new format uses attributes. This means that you cannot use any public method that contains "Tag" in the name to test the reports generated in the memory.

[!INCLUDE [send-report-xml](../developer/includes/send-report-xml.md)]

## Related information

[Reports Overview](devenv-reports.md)  
[Test pages](devenv-testing-pages.md)  
[Test Codeunits and Test Methods](devenv-test-codeunits-and-test-methods.md)
