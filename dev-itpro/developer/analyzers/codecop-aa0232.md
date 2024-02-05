---
title: "CodeCop Info AA0232"
description: "You can potentially increase performance if fields that are used in FlowFields are added to SumIndexedFields of the corresponding key."
ms.author: solsen
ms.custom: na
ms.date: 01/11/2023
ms.reviewer: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# CodeCop Info AA0232
The FlowField of a table should be indexed.

## Description
You can potentially increase performance if fields that are used in FlowFields are added to SumIndexedFields of the corresponding key.

[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Reason for the rule

> [!NOTE]  
> Be aware that this rule can, in some cases, cause false warnings even though you have addressed any performance issues by adding SIFT indices. The rule will be fixed in a future release. 

When there are performance issues on List pages, the root cause is often that they display FlowFields defined on top of tables that are inadequately indexed - these are typically missing SIFT indices. 
As any FlowField potentially can be shown on a page, make sure that they're all adequately indexed.

## Bad code example
```AL
table 18 Customer
{...
    fields
    {...
        field(97; "Debit Amount"; Decimal)
        {
            ...
            CalcFormula = Sum ("Detailed Cust. Ledg. Entry"."Debit Amount" WHERE("Customer No." = FIELD("No."),
                                                                                 "Entry Type" = FILTER(<> Application),
                                                                                 "Initial Entry Global Dim. 1" = FIELD("Global Dimension 1 Filter"),
                                                                                 "Initial Entry Global Dim. 2" = FIELD("Global Dimension 2 Filter"),
                                                                                 "Posting Date" = FIELD("Date Filter"),
                                                                                 "Currency Code" = FIELD("Currency Filter")));
            FieldClass = FlowField;
            ...
        }
        ...
    }
    keys { ... }
    ...
}
table 379 "Detailed Cust. Ledg. Entry"
{...
    fields { ... }
    keys
    {
        key(Key1; "Entry No.")
        {
            Clustered = true;
        }
    }
    ...
}
```
 
## Good code example

```AL
table 18 Customer
{...
    fields
    {...
        field(97; "Debit Amount"; Decimal)
        {
            ...
            CalcFormula = Sum ("Detailed Cust. Ledg. Entry"."Debit Amount" WHERE("Customer No." = FIELD("No."),
                                                                                 "Entry Type" = FILTER(<> Application),
                                                                                 "Initial Entry Global Dim. 1" = FIELD("Global Dimension 1 Filter"),
                                                                                 "Initial Entry Global Dim. 2" = FIELD("Global Dimension 2 Filter"),
                                                                                 "Posting Date" = FIELD("Date Filter"),
                                                                                 "Currency Code" = FIELD("Currency Filter")));
            FieldClass = FlowField;
            ...
        }
        ...
    }
    keys { ... }
    ...
}
table 379 "Detailed Cust. Ledg. Entry"
{...
    fields { ... }
    keys
    {
        key(Key1; "Entry No.")
        {
            Clustered = true;
        }
        key(Key2; "Customer No.", "Entry Type", "Initial Entry Global Dim. 1", "Initial Entry Global Dim. 2", "Posting Date", "Currency Code")
        {
            SumIndexFields = "Debit Amount"
        }
    }
    ...
}
```

## See Also  
[CodeCop Analyzer](codecop.md)  
[Get Started with AL](../devenv-get-started.md)  
[Developing Extensions](../devenv-dev-overview.md)  