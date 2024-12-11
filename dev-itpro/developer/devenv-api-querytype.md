---
title: API query type
description: Description of the API query type used for exposing and viewing web service endpoints.
author: SusanneWindfeldPedersen
ms.date: 04/17/2024
ms.topic: conceptual
ms.author: solsen
ms.reviewer: solsen
---

# API query type

Queries of the type `API` are used to generate web service endpoints and this type of query can't be used to display data in the user interface. A query of the API type can be used to join data from different data sources. The data can only be viewed. When creating this query type, you must specify a number of properties that provide information for the web service endpoint. Use the snippet `tquery - Query of type API` to get the right template and the list of these properties automatically filled in.

[!INCLUDE[intelli_shortcut](includes/intelli_shortcut.md)]

[!INCLUDE[extending_APIs_is_not_supported_note](includes/include-extending-APIs-is-not-supported-note.md)]

## Example of the API query type

The following query example publishes an API available at:
`../contoso/app1/v1.0/companies({id})/customerSales`. The `APIVersion` can be specified as one version, or a list of versions, if the API is supported through multiple versions.

```AL
query 20000 "APIV1 - Customer Sales"
{
    QueryType = API;
    APIPublisher = 'contoso';
    APIGroup = 'app1';
    APIVersion = 'v1.0';
    Caption = 'customerSales', Locked = true;
    EntityName = 'customerSale';
    EntitySetName = 'customerSales';

    elements
    {
        dataitem(QueryElement1; Customer)
        {
            column(customerId; Id)
            {
                Caption = 'Id', Locked = true;
            }
            column(customerNumber; "No.")
            {
                Caption = 'No', Locked = true;
            }
            column(name; Name)
            {
                Caption = 'Name', Locked = true;
            }
            dataitem(QueryElement10; "Cust. Ledger Entry")
            {
                DataItemLink = "Customer No." = QueryElement1."No.";
                SqlJoinType = LeftOuterJoin;
                DataItemTableFilter = "Document Type" = FILTER (Invoice | "Credit Memo");
                column(totalSalesAmount; "Sales (LCY)")
                {
                    Caption = 'TotalSalesAmount', Locked = true;
                    Method = Sum;
                }
                filter(dateFilter; "Posting Date")
                {
                    Caption = 'DateFilter', Locked = true;
                }
            }
        }
    }
}
```

## Related information

[AL development environment](devenv-reference-overview.md)  
[API page Type](devenv-api-pagetype.md)  
[APIPublisher property](properties/devenv-apipublisher-query-property.md)  
[APIGroup property](properties/devenv-apigroup-query-property.md)  
[APIVersion property](properties/devenv-apiversion-query-property.md)   
[EntityName property](properties/devenv-entityname-property.md)  
[EntitySetName property](properties/devenv-entitysetname-property.md)  
[Query object](devenv-query-object.md)  
[Developing extensions](devenv-dev-overview.md)  
