---
title: Protected variables
description: The protected keyword can be used to make variables accessible between tables and table extensions, pages and page extensions and report and report extensions.
ms.date: 05/24/2024
ms.topic: article
author: SusanneWindfeldPedersen
ms.collection: get-started
---

# Protected variables

[!INCLUDE[2019_releasewave2.md](../includes/2019_releasewave2.md)]

The `protected` keyword can be used to make variables accessible between tables and table extensions, pages and page extensions and reports and report extensions. It also makes variables accessible between extensions if they belong to apps, which depend on each other. If you want to only expose some variables as `protected`, you must create two sections of `var` declarations. See the syntax below.

## Syntax

```AL
protected var
        myInt: Integer; // protected var

var
        myLocalInt: Integer; // local var
```

## Example

The example below illustrates how to declare and use a protected variable.

```AL
page 50100 MyPage
{
    SourceTable = Customer;
    PageType = Card;

    layout
    {
        area(Content)
        {
            group(General)
            {
                field(Name; Name)
                {
                    ApplicationArea = All;
                }
            }
            group(Advanced)
            {
                Visible = ShowBalance;

                field(Balance; Balance)
                {
                    ApplicationArea = All;
                }
            }
        }
    }

    protected var
        ShowBalance: Boolean;
}

pageextension 50101 MyPageExt extends MyPage
{
    layout
    {
        addlast(Content)
        {
            group(MoreBalance)
            {
                Visible = ShowBalance; // ShowBalance from MyPage

                field("Balance (LCY)"; "Balance (LCY)")
                {
                    ApplicationArea = All;
                }
            }
        }

    }

    actions
    {
        addlast(Navigation)
        {
            action(ToggleBalance)
            {
                ApplicationArea = All;
                trigger OnAction()
                begin
                    ShowBalance := not ShowBalance; // Toggle ShowBalance from MyPage.
                end;
            }
        }
    }
}
```

## Related information

[AL method reference](./methods-auto/library.md)   
[Properties](properties/devenv-properties.md)  
[Access property](properties/devenv-access-property.md)  
[Extensible property](properties/devenv-extensible-property.md)
