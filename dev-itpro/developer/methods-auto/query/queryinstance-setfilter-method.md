---
title: "Query.SetFilter(Any, Text [, Any,...]) Method"
description: "Sets a filter on a column of a query to limit the records in the resulting data set of a query."
ms.author: solsen
ms.custom: na
ms.date: 03/02/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Query.SetFilter(Any, Text [, Any,...]) Method
> **Version**: _Available or changed with runtime version 1.0._

Sets a filter on a column of a query to limit the records in the resulting data set of a query.


## Syntax
```AL
 Query.SetFilter(Column: Any, String: Text [, Value: Any,...])
```
## Parameters
*Query*  
&emsp;Type: [Query](query-data-type.md)  
An instance of the [Query](query-data-type.md) data type.  

*Column*  
&emsp;Type: [Any](../any/any-data-type.md)  
The name of the column in the query that you want to filter. The name is defined by the column's Name Property.  

*String*  
&emsp;Type: [Text](../text/text-data-type.md)  
The filter expression. A valid expression consists of alphanumeric characters and one or more of the following operators: \<, \<=, \>, \>=, \<\>, &, .., *, &#124; and @. You can use replacement fields (%1, %2, and so on) to insert values at runtime.  

*[Optional] Value*  
&emsp;Type: [Any](../any/any-data-type.md)  
Replacement values to insert in replacement fields in the filter expression. The data type of Value must match the data type of field that is referred to by the ColumnName.  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  
 To apply filters to a dataset, the **SetFilter** method must be called before the **Open**, **SaveAsXML**, and **SaveAsCSV** methods, as shown in the following example. To remove filters from query, you call the [Clear Method](../library.md).  
  
```al
Query.SetFilter(Column1, String);  
Query.Open;  
Query.Read;  
Clear(Query);  
```  
  
 A call to the **SetFilter** method automatically closes a query dataset that is currently open. Therefore, the following code is unauthorized and will fail because there is no open dataset for the **Read** method to read.  
  
```al
Query.Open;  
Query.Read;  
Query.SetFilter(Column2, String);  
Query.Read;  
```  
  
 You can have multiple calls to the **SetFilter** method. If **SetFilter** method calls set filters on different columns, then the filters are combined and applied to the dataset. If consecutive **SetFilter** method calls set filters on the same column, then the last **SetFilter** method call is applied to the column.  
  
 In addition to the **SetFilter** method, you can apply filters to a query using the [SetRange Method \(Query\)](../library.md) method, the **FilterGroup** method, and the [DataItemTableFilter Property](/dynamics365/business-central/dev-itpro/developer/properties/devenv-dataitemtablefilter-property) and [ColumnFilter Property](../../properties/devenv-columnfilter-property.md).  
  
|If the **SetFilter** method...|then...|  
|--------------------------------------|-------------|  
|Sets a filter on the same field as the **DataItemTableFilter** property|The two filters are joined into a resulting filter.|  
|Sets a filter on the same field as the **ColumnFilter** property|The **SetFilter** method overwrites the **ColumnFilter** property, so the filter that is set by the **SetFilter** method that is applied to the dataset.|  
|Sets a filter on the same field as the **SetRange** method|The method that is called last is applied to the dataset.|  
|Sets a filter on a field that has global filters that are applied by the **FilterGroup\(1\)** method|The filters of the **SetFilter** method are added to the global filters.|  
  
 For example, a query has the following filters set on the **Quantity** column:  
  
-   **DataItemTableFilter** property: Quantity=Filter\(\<100\)  
  
-   **ColumnFilter** property: Quantity=Filter\(\<>50\)  
  
 `Query.SetFilter ("Quantity", '>1')` will result in a filter that is equivalent to: 1\<Quantity \<100.  
  
 <!--Links For more information about how to set filters in Query Designer, see [Understanding Query Filters](Understanding-Query-Filters.md).-->  
  
## Example  
 The following AL code example demonstrates how to use the **SetFilter** method on a query. The example code sets a filter on a query column, and then displays a message when the query is run that indicates the filter on the column.  
  
 This example requires that you create a query called **Customer\_SalesQuantity** that has the following characteristics:  
  
  -   Links table 18, Customer with table 37, Sales Lines from the [!INCLUDE[demolong](../../includes/demolong_md.md)].  

  -   Includes columns for the **Name** and **No.** fields from the **Customer** table and the **Quantity** field from **Sales Lines** table.  

        <!--NAV For step-by-step instructions for creating this query, see [Walkthrough: Creating a Query to Link Two Tables](Walkthrough--Creating-a-Query-to-Link-Two-Tables.md).-->  
  
```al
var
  MyQuery: Query "Customer SalesQuantity";
  Text000: Label 'Customer name = %1, Quantity = %2';
begin
    // Sets a filter to display only sales quantities greater than 10.  
    MyQuery.SetFilter(Quantity, '>10');  
    // Sets a filter to display the columns with the value Selangorian Ltd. only.  
    MyQuery.SetFilter(NAME, 'Selangorian Ltd.');  
    // Runs the query.  
    MyQuery.Open;  
    // Reads each row in the dataset and displays message with column values.  
    // Stops reading when there are no more rows remaining in the dataset (Read is False).  
    while MyQuery.Read do  
    begin  
      Message(Text000, MyQuery.Name, MyQuery.Quantity);  
    end;   
    // Saves the resulting dataset as a CSV file.  
    MyQuery.SaveAsCSV('c:\temp\CustomerSales.csv');  
    // Closes the query.  
    Myquery.Close; 
end;
```  
  
 When the code is run, a message that resembles the following appears for each row in the dataset:  
  
 **Customer name = Selangorian Ltd., Quantity = 30**

## See Also
[Query Data Type](query-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)
