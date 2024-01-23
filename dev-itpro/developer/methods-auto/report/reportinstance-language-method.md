---
title: "Report.Language([Integer]) Method"
description: "Gets or sets the current language setting for the report."
ms.author: solsen
ms.custom: na
ms.date: 04/17/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Report.Language([Integer]) Method
> **Version**: _Available or changed with runtime version 1.0._

Gets or sets the current language setting for the report.


## Syntax
```AL
[CurrentLanguage := ]  Report.Language([Language: Integer])
```
> [!NOTE]
> This method can be invoked using property access syntax.
## Parameters
*Report*  
&emsp;Type: [Report](report-data-type.md)  
An instance of the [Report](report-data-type.md) data type.  

*[Optional] Language*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The new language setting for the report.  


## Return Value
*[Optional] CurrentLanguage*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The current language setting for the report.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Example

If you have reports that you want to print in the language of the recipient rather than in your own working language, you can add a single line of code in the report to handle this. This functionality is already enabled for most reports in the standard Business Central[!INCLUDE [prod_short](../../includes/prod_short.md)] database. The document is printed in the language that is specified in the **Language Code** field on the **Customer Card** page.

For reports that need the multiple document languages functionality, you must insert the following AL code as the first line in the `OnAfterGetRecord()` trigger on the data item referencing the **Customer** table (notice that that feature isn't limited to the **Customer** table, other data sources provides similar functionality):

`CurrReport.Language := LanguageMgmt.GetLanguageIdOrDefault("Language Code");`

For each of these reports, you must create a new variable, `LanguageMgmt`, with the data type `Codeunit` pointing to the `Language` codeunit. When you have compiled the object, it'll no longer print in the user's working application language if another language has been specified on the **Customer Card** page.

```AL
var
    LanguageMgmt: Codeunit Language;
```

## See Also

[Report Data Type](report-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  
[Report Localization](../../devenv-report-localization.md)  
[Report.FormatRegion](./reportinstance-formatregion-method.md)
