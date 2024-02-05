---
title: "Query.GetFilter(Any) Method"
description: "Returns the filters that are set on the field of a specified column in the query."
ms.author: solsen
ms.custom: na
ms.date: 03/24/2022
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Query.GetFilter(Any) Method
> **Version**: _Available or changed with runtime version 1.0._

Returns the filters that are set on the field of a specified column in the query. The following code shows the syntax of the GETFILTER method. Query is a variable of the Query data type that specifies the query object.


## Syntax
```AL
Filter :=   Query.GetFilter(Column: Any)
```
## Parameters
*Query*  
&emsp;Type: [Query](query-data-type.md)  
An instance of the [Query](query-data-type.md) data type.  

*Column*  
&emsp;Type: [Any](../any/any-data-type.md)  
The name of the column in the query. A column name is defined by the Name Property.  


## Return Value
*Filter*  
&emsp;Type: [Text](../text/text-data-type.md)  
The filters of the column.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  
 The **GetFilter** method returns the filters that are currently set for a data column or filter row by the [SetFilter Method \(Query\)](../../methods-auto/query/queryinstance-setfilter-method.md) method, [SetRange Method \(Query\)](../../methods-auto/query/queryinstance-setrange-method.md) method, and the column's [ColumnFilter Property](../../properties/devenv-columnfilter-property.md). The **GetFilter** method does not return filters that are set on a column's source field by the [DataItemTableFilter Property](/dynamics365/business-central/dev-itpro/developer/properties/devenv-dataitemtablefilter-property) or global filters that are set by the **FilterGroup** method.  

  
 You can call the **GetFilter** method multiple times and at any point in the code. If you call the **GetFilter** method before the **SetFilter** or **SetRange** method, then the **GetFilter** method returns only filters on the column that are set by the column's ColumnFilter property.  
  
 Filters that are set by the **SetFilter** method and **SetRange** method are applied to a query when the query is opened with a call to the **Open**, **SaveAsXML**, or **SaveAsCSV** methods. You must consider the location of the **GetFilterS** method with respect to these methods to obtain the desired results. For example, in the following two code examples, the **GetFilter** method will return the filter that is set by the **SetFilter** method. However, in the first example, the filter has been applied to the query dataset; in the second example, the filter has not been applied.  
  
```al
Query.SetFilter(Column, String);  
Query.Open;   
Query.GetFilter(Column);  
Query.Read;  
```  
  
```al
Query.Open;   
Query.SetFilter(Column, String);  
Query.GetFilter(Column);  
Query.Read;  
```  
  
## Example  
 The following AL code example demonstrates how to use the **GetFilter** method on a query. The example code sets a filter on a query column, and then displays a message when the query is run that indicates the filter on the column.  
  
 This example requires that you create a query called **Customer\_SalesQuantity** that has the following characteristics:  
  
-  Links table **18 Customer** with table **37 Sales Lines** from the CRONUS International Ltd. demonstration database.  

-   Includes columns for the **Name** and **No.** fields from the **Customer** table and the **Quantity** field from **Sales Lines** table.  
  
<!--NAV For step-by-step instructions for creating this query, see [Walkthrough: Creating a Query to Link Two Tables](Walkthrough--Creating-a-Query-to-Link-Two-Tables.md).-->  
  
-   The ColumnFilter property of the **Quantity** column is set to include values greater than 5.  
  
 The following AL code runs the query and displays a message that contains the filter that is set on a query column. You can add the code to a codeunit, and then run the codeunit to see the results.  
  
  
```al
var
    MyQuery: Query "Customer SalesQuantity";
    MyFilter: Text;
    Text000: Label 'The filter is: %1';
begin
    // Sets a filter to display only sales quantities greater than 10. This overwrites the ColumnFilter property.  
    MyQuery.SetFilter(Quantity, '>10');  
    // Runs the query and applies the filter.  
    MyQuery.Open;  
    // Returns the filter on the Quantity column and displays the filter in a message.  
    MyFilter := MyQuery.GetFilter(Quantity);  
    Message(Text000, MyFilter);  
end;
```  
  
 Running the code returns the following message:  
  
 **The filter is: Quantity > 10**

## See Also
[Query Data Type](query-data-type.md)  
[Get Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)
