---
title: "QueryCategory Property"
ms.date: 10/29/2020
ms.suite: na
ms.topic: article
ms.author: solsen
---
 
# QueryCategory Property

This property is used to indicate a given query can be made available as views displayed on certain main entity lists. With this functionality, you can create your own queries through extensions and then have them assigned to a main list page by setting the QueryCategory property. This way you can direct users to related information based on a query even where the data is not coming from a single table.

On queries, the QueryCategory property specifies one or more query categories that the object supports. On pages, QueryCategory specifies the query category that the page supports.

## Applies to  

- Queries
- Pages

## Syntax

```al
query 50100 QueryWithCategories
{
    QueryType = Normal;
    QueryCategory = 'Customer', 'Items';

    elements
    {
        dataitem(DataItemName; Customer)
        {
            column(ColumnName; Name)
            {

            }

        }
    }

    var
        myInt: Integer;

    trigger OnBeforeOpen()
    begin

    end;
}
```

```al
page 50111 CustomerSourceTable
{
    PageType = List;
    ApplicationArea = All;
    UsageCategory = Administration;
    SourceTable = Customer;
    QueryCategory = 'Customer';

    layout
    {
        area(Content)
        {
            group(GroupName)
            {
                field(Name; Name)
                {
                    ApplicationArea = All;

                }
            }
        }
    }

    actions
    {
        area(Processing)
        {
            action(ActionName)
            {
                ApplicationArea = All;

                trigger OnAction()
                begin

                end;
            }
        }
    }
}
```

## Remarks

For the syntax examples above, when page **CustomerSourceTable** is opened in the client, query **QueryWithCategories** will be available as a view. **QueryWithCategories** could also be used on other pages by setting the QueryCategory of the pages to either `'Customer'` or `'Items'`.

## See Also

[Properties](devenv-properties.md)   
[Query Object](../devenv-query-object.md)  
[Page Object](../devenv-page-object.md)
