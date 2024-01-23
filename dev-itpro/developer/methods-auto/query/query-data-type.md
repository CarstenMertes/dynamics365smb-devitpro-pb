---
title: "Query Data Type"
description: "Enables you to retrieve data from multiple tables and combine the data in single dataset."
ms.author: solsen
ms.custom: na
ms.date: 12/01/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Query Data Type
> **Version**: _Available or changed with runtime version 1.0._

Enables you to retrieve data from multiple tables and combine the data in single dataset.


## Static methods
The following methods are available on the Query data type.


|Method name|Description|
|-----------|-----------|
|[SaveAsCsv(Integer, Text [, Integer] [, Text])](query-saveascsv-integer-string-integer-string-method.md)|Saves the resulting data set of a query as a comma-separated values (CSV) file.|
|[SaveAsCsv(Integer, OutStream [, Integer] [, Text])](query-saveascsv-integer-outstream-integer-string-method.md)|Saves the resulting data set of a query as a comma separated values (CSV) file.|
|[SaveAsXml(Integer, Text)](query-saveasxml-integer-string-method.md)|Saves the resulting data set of a query as an .xml file.|
|[SaveAsXml(Integer, OutStream)](query-saveasxml-integer-outstream-method.md)|Saves the resulting data set of a query as an .xml file.|

## Instance methods
The following methods are available on instances of the Query data type.

|Method name|Description|
|-----------|-----------|
|[Close()](queryinstance-close-method.md)|Closes a query data set and returns the query instance to the initialized state. The following code shows the syntax of the CLOSE method.  Query is a variable of the Query data type that specifies the query object.|
|[ColumnCaption(Any)](queryinstance-columncaption-method.md)|Returns the current caption of a query column as a text string.|
|[ColumnName(Any)](queryinstance-columnname-method.md)|Returns the name of a query column as a text string.|
|[ColumnNo(Any)](queryinstance-columnno-method.md)|Returns the ID that is assigned to a query column in the query definition.|
|[GetFilter(Any)](queryinstance-getfilter-method.md)|Returns the filters that are set on the field of a specified column in the query. The following code shows the syntax of the GETFILTER method. Query is a variable of the Query data type that specifies the query object.|
|[GetFilters()](queryinstance-getfilters-method.md)|Returns the filters that are applied to all columns in the query. The following code shows the syntax of the GETFILTERS method. Query is a variable of the Query data type that specifies the query object.|
|[Open()](queryinstance-open-method.md)|Runs a query object and generates a data set that can be read. The following code shows the syntax of the OPEN method. Query is a variable of the Query data type that specifies the query object.|
|[Read()](queryinstance-read-method.md)|Reads data from a row in the resulting data set of a query.|
|[SaveAsCsv(Text [, Integer] [, Text])](queryinstance-saveascsv-string-integer-string-method.md)|Saves the resulting data set of a query as comma separated values (CSV)|
|[SaveAsCsv(OutStream [, Integer] [, Text])](queryinstance-saveascsv-outstream-integer-string-method.md)|Saves the resulting data set of a query as comma separated values (CSV)|
|[SaveAsXml(Text)](queryinstance-saveasxml-string-method.md)|Saves the resulting data set of a query as XML|
|[SaveAsXml(OutStream)](queryinstance-saveasxml-outstream-method.md)|Saves the resulting data set of a query as XML|
|[SecurityFiltering([SecurityFilter])](queryinstance-securityfiltering-method.md)|Gets or sets how security filters are applied to the query.|
|[SetFilter(Any, Text [, Any,...])](queryinstance-setfilter-method.md)|Sets a filter on a column of a query to limit the records in the resulting data set of a query.|
|[SetRange(Any [, Any] [, Any])](queryinstance-setrange-method.md)|Sets a filter on a range of values on a column of a query data set.|
|[TopNumberOfRows([Integer])](queryinstance-topnumberofrows-method.md)|Specifies the maximum number of rows to include in the resulting data set of a query.|

[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)  